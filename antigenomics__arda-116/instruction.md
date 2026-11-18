# Issue

**Title:** feat: AIRR umi_count, and the dnaio premise that blocked it

## Description

S4 of `project/design-singlecell.md` was parked as *"blocked on a migec format decision, not on arda"*. It was not blocked — the analysis was answering a different question from the one AIRR's field asks.

## Why it was never blocked

> `umi_count` — Number of **distinct UMIs** represented by this sequence.

Distinct UMIs, not distinct records. The old blocker read `.<m>` as a molecule index and concluded the count was unreconstructable. `.<m>` *is* a flat index over (component × split) — but both conditional suffixes subdivide reads that **already share one `<umi>`**, so no reading of them can change a distinct-UMI count. `<sample>`, `<cell>` and `<umi>` are written unconditionally.

The old blocker is real, but it is about *molecule identity* — joining a record to its row in `<sample>.mig.tsv`. Nothing in `umi_count` needs that join.

## Measured, not reasoned

The first draft of the rescope reasoned about when `umi_count` would differ from `consensus_count` and **got it wrong**. Re-done against real `migec assemble` output:

| case | result |
|---|---|
| **saturated barcode** — migec splits one barcode into two molecules on minor-allele linkage, positions outside the junction | `duplicate_count 3, consensus_count 3, **umi_count 2**` |
| **contig mode** — 12 reads on `[0,170)` + 12 on `[230,400)` of one molecule | `consensus_count == umi_count == 2` — no difference |

Contig mode does not produce the inequality: `place_reads` never extends a component across a gap, so two contigs of one molecule do not overlap and at most one carries a complete junction; the rest are dropped by `complete_only`. The design record now says what was measured.

## What ships

- `correct --cell-from` / `--cell-regex`, the pair `map` already took → `umi_count` in `clones.tsv`
- **Omitted, not 0 or 1**, when the dialect names no UMI (`cellranger`/`prefix`/`--cell-regex` carry a cell and no UMI) or the ids do not parse — QC trap 4
- **Both-halves flag.** Stage 1 needs `--cell-from` for `cell_id`; Stage 2 derives `umi_count` from `sequence_id` itself and cannot get it from Stage 1's output. `cluster.regime_flags` sends it to both, with a test — passed to one half only, a sharded run silently drops a column.
- Appended **last**, after the chimera column, so `d_call` never moves.

## Also

**A wrong premise about dnaio, recorded in four places** (`cell.py`, `cli.py`, `map.py`, and `migec/src/assemble.cpp`): all said the FASTQ comment cannot reach arda because dnaio drops it. It does not — `SequenceRecord.comment` carries the whole tag string. arda drops it by taking `.id`. Nothing behavioural changes, but migec's `cD:i:` per-consensus read depth is a field away rather than unreachable.

**Two stale open loops closed.** `v_identity` is neither gated nor deleted — no threshold (the target-inverted rows it separates are refused structurally in both reductions, and this repo ships no QC threshold), not deleted (2.16.0 made it the framework-scoped V identity with its own verification recipe in `docs/shm.rst`). `_SEGMENT_FORMAT` already carries `tend` and `_segment_rows` already filters `tstart <= tend`.

## Verification

- `tests/unit/test_umi_count.py` — 9 tests, shapes taken from real migec output
- `test_regime_flags_sends_cell_from_to_BOTH_halves`
- 1,105 passed, 9 skipped (was 1,095); `ruff check src/` clean; `sphinx-build -W` zero warnings

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43b7fa8ae8ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.