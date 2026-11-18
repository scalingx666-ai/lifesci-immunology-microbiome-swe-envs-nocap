# Issue

**Title:** Count only the pairs actually solved on the raster polygon path

## Description

Addresses the remaining behavior reported on #341.

## What's wrong

#449 fixed the include/exclude pairs file so it actually restricts which pairs are solved, but raster pairwise has two code paths and the fix only completed one of them. When focal nodes span multiple cells (patches/"cores"), `_pt_file_polygons_path` still computed its progress count **before** filtering — `calc_num_pairs` was a plain C(n,2) over every node mentioned in the include file — and logged `Solving pair k of n` **before** the exclude check, so excluded pairs were reported as being solved.

The results were correct; only the log was wrong. But it's a misleading log: users reasonably conclude the feature is broken, and at least one reporter aborted a run they believed would OOM.

This is exactly the July 2026 report on the issue:

- include file `1 6` / `1 10` → `Total number of pair solves = 3` while solving two (6–10 correctly `-1`)
- 292 focal nodes → `42486`, which is C(292,2)

Reproduced locally with the same include file (`1 2` / `1 3`, four nodes) through both paths:

| Path | Before | After |
|---|---|---|
| single-cell nodes | `pair solves = 2` | `pair solves = 2` |
| multi-cell regions | `pair solves = 3`, `Solving pair 1 of 3 … 3 of 3` | `pair solves = 2`, `Solving pair 1 of 2`, `2 of 2` |

Result matrices are identical before and after.

## Fix

- Replace `calc_num_pairs` with `pairs_to_solve(pts, exclude_pairs)`, which returns the filtered `(i, j)` index pairs. Count that, and iterate over it so the log line sits inside the loop of pairs that are actually solved.
- Look exclusions up in a `Set` rather than a `Vector`. The old loop did two `in` scans on a `Vector` per pair; with the ~41k-entry exclude lists the reporters describe that was O(pairs × exclusions).
- Gate the resistance-shortcut log lines in the AMG solver (`src/core.jl`) on the `log` flag, like the pair-count line already is. Each polygon-path pair solve calls the solver with `log=false`, and these lines were emitting a nested `Total number of pair solves has been reduced to 1` for every pair, which made the count even more confusing.

## Tests

Four new assertions on `pairs_to_solve` in `test/issue341.jl`: include-style exclusion in both orders, no exclusions, a pair listed in only one order, and non-contiguous unsorted node IDs. The existing polygon-path end-to-end case (Test 4) still verifies the result matrix.

Log capture isn't practical here since `compute` installs its own global logger, so the count is tested at the helper level.

Full suite with `JULIA_NUM_THREADS=4`: Unit 17/17, CG+AMG 719/719, CHOLMOD 719/719, Issue 341 **28/28** (was 24).

## Not in this PR

Two adjacent gaps found while reading, filed separately from this fix:
- Network mode ignores the include file entirely (`get_network_data` never reads `use_included_pairs`; `network/pairwise.jl` hard-codes an empty exclude list), despite `docs/src/options.md` saying the feature affects all modes except advanced.
- One-to-all/all-to-one indexes the include matrix by point-file scan order but the matrix rows are in sorted-ID order (`src/raster/onetoall.jl:82-84`). Suspected, not reproduced.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ede3998f2a8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.