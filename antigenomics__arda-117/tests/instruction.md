# Issue

**Title:** feat: arda scenarios — a recombination model estimated from junctions

## Description

ROADMAP's *"Nucleotide junction re-mapping → recombination-scenario counts"*.

`arda.dpost` places a D from an amino-acid junction by marginalising a generative model whose every number is **borrowed from OLGA/vdjrearm** and shipped as `database/vdj/<org>/d_prior.tsv`. This is how arda estimates its own, from its own output.

```bash
arda scenarios -i sample.clones.tsv -o my_prior.tsv --organism human
```

Same long `locus / kind / key / value` table, same key grammar — a **drop-in** for the shipped file, plus `delV` / `delJ` which nothing shipped because nothing produced them. A test writes the output and reads it back through `dpost.load_d_prior`, because "drop-in" is the one property the module exists for.

## Why expected counts, not a MAP reading

A scenario is **not identifiable from sequence** — **4,346** tuples reproduce one real human TRB junction exactly. A first non-templated base that happens to match germline is indistinguishable from one less nucleotide of trimming, the same ambiguity `CLAUDE.md` already forbids "fixing" inside a junction.

So the tallies are expected counts summed over scenarios under the current model. Counting one MAP reading assigns weight 1 to one member of the ambiguity set and 0 to the rest, biasing every distribution toward less trimming and shorter inserts. Weight + expected counts + renormalisation is EM — and it is the same E-step `arda.hmm` (the next roadmap item) will reuse.

## The degeneracy that makes or breaks it

**An insertion costs its own sequence (`0.25^len`), not just its length.** The junction's 5′ end reads either as templated V or as an insertion that happens to match V germline — with a length term alone the second is *free*.

| | `insVD` mass | log-likelihood |
|---|---|---|
| without the term | walks to **10–11 nt** | rises monotonically the whole way |
| with the term | peaks at **4 nt** | converges in ~4 passes |

Measured on 503 real human TRB junctions. With the term, `dlen` for `TRBD1*01` peaks at **4–5 surviving nt** — independently reproducing the *"median surviving D is 5 nt for human TRB"* figure already measured in `dpost`. A test pins the direction by monkeypatching the constant.

## Other invariants held

- `dlen == 0` (D trimmed away) is enumerated — dropping those records truncates `dlen` at 1 and inflates every insertion distribution by the length of the D that was really there
- VJ loci are not skipped: no D and no `insDJ`, but they carry most of the trimming evidence
- Each record contributes **1.0 in total**, not one count per scenario
- `--weight` is stated in the output header, not defaulted silently
- Generating a prior is **not adopting one** — the shipped `d_prior.tsv` is unchanged

V and J flanks are conditionally independent given the D placement, so each is summed once per span instead of once per (V, D, J) triple: 2,357 records over 7 loci, 4 EM iterations, in seconds.

## Verification

`tests/unit/test_scenarios.py` — 8 tests, the first being that **every** enumerated scenario reassembles its junction exactly. 1,113 passed, 9 skipped (was 1,105); `ruff` clean; `sphinx-build -W` zero warnings. New page: [scenarios](docs/scenarios.rst), design record `project/design-scenarios.md`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1af4be4dc65b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.