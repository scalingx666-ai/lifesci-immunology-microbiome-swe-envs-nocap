# Issue

**Title:** Run the test suite in single precision for every solver

## Description

Stacked originally on #486 (now merged); based on master.

`runtests(precision=...)` existed but `runtests.jl` only ever called Float64, so single precision could break without CI noticing — and it had: on master every Float32 run aborted on the hard-coded `1e-4` gate (). #256 was closed without a guard. This adds a Float32 pass for **CG+AMG, CHOLMOD and Apple Accelerate** (Pardiso is double-only).

## Harness fixes (no change to what Float64 checks)
- **Raster Advanced** called `compare_all_output` without `is_single`, so it always used the Float64 map tolerance.
- **Branch/node current files** omit zero-current rows; in Float32 a reference current of ~1e-9 rounds to exactly 0 and its row is dropped, so the files differed in length and `sortslices` threw `DimensionMismatch`. Compared by node key now, missing = 0.
- **Resistances** compare relatively (2%) in single precision. `sgVerify17` (resistances up to ~2900) comes out 1.03% off in Float32, identically at residual gates of `1e-3`/`1e-4`/`1e-5`, so it is Float32 arithmetic rather than convergence, and an absolute threshold of 0.01 is meaningless at that scale. The 2% is calibrated on this test set, not a general bound; `compute.md` gets a paragraph saying what to expect and to verify against double.

## Direct solvers: iterative refinement
Enabling CHOLMOD and Accelerate in Float32 exposed the same failure in both: a Float32 Cholesky solve of an ill-conditioned Laplacian lands at 1e-3..1e-2 — `residual 0.00199 exceeds tolerance 0.001` on `sgVerify17`, and advanced-mode maps 0.2% off where CG (with its 1e-5 `rtol`) passes. `refine_columns!` applies iterative refinement with the existing factor — refine toward `min(tol, 1e-5)`, at most two steps, error only if still above `tol` — shared by the CHOLMOD and Accelerate methods. Double precision residuals are far below the target and take no steps. Pardiso already runs `SOLVE_ITERATIVE_REFINE`.

## Results (4 threads)
| suite | Float64 | Float32 |
|---|---|---|
| CG+AMG | 719/719 | 719/719 |
| CHOLMOD | 719/719 | 719/719 |
| Accelerate | 719/719 | 719/719 |

Unit 60/60, Issue 341 46/46.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3271ae84706b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.