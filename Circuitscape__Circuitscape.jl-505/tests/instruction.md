# Issue

**Title:** Build the graph once in one-to-all/all-to-one with include pairs

## Description

Part of the unreleased 6.0.

## The problem

With `use_included_pairs = True`, the per-point function `f(i)` in `onetoall_kernel` (`src/raster/onetoall.jl`) zeroed the excluded points in a copy of `point_map` and then called `create_new_polymap`, `construct_node_map` and `construct_graph` again for every focal point. That is the whole load-time cost of the run repeated P times, and under `parallelize` all P copies are live at the same time.

Reading the code, the rebuild was also not doing what it looked like it did:

- the rebuilt graph `a` was never used: `G` and `cc` were captured from the outer scope, so every solve used the Laplacian built once outside `f`;
- the nodemap was built from `polymap` (the raw polygon file), not from the freshly built `newpoly`, so the merging of focal regions into single nodes was dropped.

What actually differs per focal point is only the set of focal *nodes* acting as sources/grounds. Whether the graph topology changes depends on the focal points:

- **single-cell focal points**: an inactive point is still an ordinary node, so the nodemap/graph/Laplacian built once are valid for every solve. Here the old inner nodemap was identical to the outer one (a single-cell label merges nothing), so the rebuild was pure waste and results were correct.
- **focal regions** (a point spanning several cells): a region collapses into one node only while it is active, so the topology depends on which points are active and a rebuild per point is needed. Here the old code was wrong: the inner nodemap (regions unmerged) disagreed with the outer `G` (regions merged), so the wrong cells were grounded. On a 6x6 grid with three two-cell regions, one-to-all with an include file listing every pair gave `[0.66, 0.39, 0.98]` where the same job with no include file gives `[0.99, 1.09, 1.24]`.

## The change

- Compute `point_file_no_polygons = length(points_rc[1]) == length(points_unique)` once (the same test `raster_pairwise` uses).
- When true, `f` reuses the outer `newpoly`, `nodemap`, `G` and `cc` and only recomputes the source/ground vectors per point. A comment explains why this is exact.
- When false (focal regions), `f` rebuilds per point as before, but correctly: nodemap from `newpoly`, and `G`/`cc` rebuilt from the new graph so numbering and Laplacian agree.
- `check_node` indexed `points_rc` by the unique-point index `i`, which only coincides with a row of `points_rc` for single-cell points; it now looks the cell up by node ID. (Gold results unaffected: for single-cell points the two indices are equal.)

## Measurements

500x500 random-resistance grid, 30 single-cell focal points, one-to-all, `use_included_pairs = True` with an exclude-mode file naming 3 pairs (exclude mode so all 30 points stay active; include mode prunes every point the file does not name), 8 neighbours, cg+amg. Measured on the rebased tree with master's `onetoall.jl` swapped in for "old". Taken while other test suites were running on the machine, so wall-clock is noisy; `@allocated` is the more reliable number. Best-of-3 of `compute(ini)`.

| mode | `@allocated` old | `@allocated` new | best-of-3 old | best-of-3 new |
|---|---|---|---|---|
| serial | 5.33 GiB | 4.35 GiB | 2.50 s | 2.32 s |
| parallel (4 threads) | 5.45 GiB | 4.38 GiB | 1.08 s | 1.01 s |

Result matrices are byte-identical old vs new. The remaining cost is the per-point solve itself.

## Tests

- Full suite green: `Unit tests 505/505`, `CG+AMG parallel Float64/Float32 685/685`, `CHOLMOD parallel Float64/Float32 685/685`, `Issue 341: included pairs 54/54` (ArchGDAL absent locally, so GeoTIFF fixtures skipped as expected). The one-to-all (13) and all-to-one (12) gold cases, including include-pairs cases 12/13, pass unchanged.
- New test in `test/issue341.jl` (Test 13) for focal regions + include file in one-to-all: including every pair must reproduce the no-include-file result, and with only (1,2),(1,3) included, the result for point 2 must equal the raster that simply lacks region 3 (and likewise for point 3 / region 2). The old code fails this test.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62187e8845e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.