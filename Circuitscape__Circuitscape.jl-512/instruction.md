# Issue

**Title:** Hold fewer copies of the Laplacian during pairwise solves

## Description

## Summary
- Extract each connected component's submatrix lazily inside the component loop instead of building all of them up front. A single-component raster now reuses the graph matrix without copying.
- Pass the diagonal regularization to CHOLMOD through `cholesky(...; shift=...)` instead of materializing `matrix + sparse(10eps*I)`. The residual check in `refine_columns!` still uses the unshifted matrix, so results are bit-identical.
- Remove a dead `deepcopy` in the advanced-mode solver.

Wrapping the matrix in `Symmetric` or passing only the lower triangle was measured and not adopted: Julia's CHOLMOD conversion copies all nonzeros either way, so peak memory did not move.

## Measurements
Synthetic 1000x1000 raster, 4 focal points, 4 threads, results bit-identical:

| run | peak RSS before | peak RSS after | time before | time after |
|---|---|---|---|---|
| CHOLMOD double | 2947 MiB | 2564 MiB | 2.60 s | 1.88 s |
| CHOLMOD single | 2308 MiB | 2097 MiB | 2.52 s | 1.98 s |
| CG+AMG double | 3042 MiB | 2935 MiB | 2.69 s | 2.06 s |

## Not covered
- The Accelerate extension still builds a shifted copy; its public API has no shift option.
- The Pardiso extension rebuilds the shifted matrix on every batch. Not changed because MKL is unavailable for testing.

## Test plan
- [x] `Pkg.test()`: unit, CG+AMG and CHOLMOD suites in double and single all pass. Accelerate, Pardiso and GeoTIFF suites skipped (packages not installed).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1139e772a068`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.