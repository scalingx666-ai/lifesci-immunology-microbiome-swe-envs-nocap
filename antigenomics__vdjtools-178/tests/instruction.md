# Issue

**Title:** 3.3.0 — model.viterbi (argmax of the Pgen DP) + generate(seed=) determinism fix

## Description

## `vdjtools.model.viterbi` — the argmax side of the Pgen DP

`pgen_nt` **sums** over every recombination that could produce a nucleotide CDR3. `best_scenario(model, cdr3_nt, v=, j=)` takes the **maximum** over the same loops and returns the single most likely one — which *is* the V/D/J boundary markup.

```python
from vdjtools.model import best_scenario
sc = best_scenario(model, "TGTGCCAGCAGCTTAGGGACAGGGGGCTACGAGCAGTACTTC",
                   v="TRBV19*01", j="TRBJ2-7*01")
sc.v_end, sc.d_call, sc.d_start, sc.d_end, sc.j_start   # -> 8, 'TRBD1*01', 15, 24, 26
```

It re-derives nothing — every probability comes from `prepare()`'s tables, and the D placement is a max-product mirror of `pgen._d_middle` over the same `P(D|J)·P(delD|D)·Pins(VD)·Pins(DJ)` terms.

⛔ **The D therefore obeys `P(D|J)`.** TRBD2 lies 3′ of the whole TRBJ1 cluster, so that pair is genomically impossible and the model encodes it as zero. An earlier draft chose D by longest exact substring and ignored `j` entirely — it would have called the impossible pair. Regression test included.

Validated on 200–500 generated draws per locus: V span **is** the V germline, J span the J germline, D span the D germline, `scenario_p ≤ pgen_nt` (a max cannot exceed the sum it is taken over), and `scenario_p` recomputes exactly from the reported path's own table entries.

⛔ `infer_nt` (amino-acid → nucleotide) is **not implemented and raises** rather than dispatching to the oracle. Enumeration is a median 5.3×10⁶ (TRA) / 1.9×10⁷ (TRB) candidates per VDJdb record, and pinning the germline flanks to shrink it is **unsound** — it drops sequences whose germline was trimmed, and the true maximum can be one of them (caught against the brute-force oracle on `CAVSDMRF`). It needs a max-product DP with traceback.

## Fixed — `generate(model, n, seed=)` was not reproducible across processes

Same seed, same wheel, a **new interpreter → a different draw**. Within one process it looked perfect, which is why nothing caught it.

Root cause: **`collapse_alleles`** (run by `load_bundled(collapse=True)` by default) built its tables with unordered polars `group_by().agg()` — a multithreaded hash aggregation, so the collapsed table's **row order varied per process**; `_cum` then assigned the same cumulative interval to a different allele. `_pick`/`default_rng` were correct throughout.

⚠ **Not hash randomisation** — `PYTHONHASHSEED=0` did not help, which is what ruled it out. Same class as the nondeterminism recorded against arda's `correct` stage.

Fixed with `maintain_order=True` on all 12 `group_by` calls in `collapse.py` and all 7 in `generate.py`. Identical across 5 separate processes on TRA, TRB and IGH. New tests run the sampler in a **subprocess** (in-process it agrees even with the bug) and fail 4 of 5 without the fix.

⛔ **This changes generated output for a given seed** — necessarily, since the old order was arbitrary. Any expectation recorded from `generate()` before 3.3.0 must be re-derived; nothing in the suite depended on one.

## Also

- `arda-mapper` pinned **>=2.19.0** (was >=2.5.5).
- Version 3.3.0 in **both** `pyproject.toml` and `__init__.py` — `test_smoke::test_version` caught the drift, which is what it is for.
- Docs: `model.viterbi` in `docs/api.rst`, API surface in `skills/vdjtools/SKILL.md`, README example whose printed output was verified against the **built wheel**.

## Verification

**538 passed**, 24 skipped, 0 failed. `sphinx -W` builds clean. Wheel built and smoke-tested in a fresh 3.12 venv.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8a6957fb8c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.