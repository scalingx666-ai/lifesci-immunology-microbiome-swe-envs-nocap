# Issue

**Title:** Upgrade to AlgebraicMultigrid 2, TimerOutputs 1, GZip 0.7, AppleAccelerate 0.7

## Description

## Summary

Bumps four dependencies that had newer versions available, and fixes the one source-level break that the AlgebraicMultigrid upgrade caused.

| Package | Before | After |
| --- | --- | --- |
| AlgebraicMultigrid | `1.2` | `2` |
| TimerOutputs | `0.5` | `1` |
| GZip | `0.6` | `0.7` |
| AppleAccelerate | `0.6` | `0.7` |

`ArchGDAL`, `Krylov`, `Pardiso`, `Graphs`, and `DelimitedFiles` are already at their latest available versions, so their bounds are unchanged.

Version bumped to 5.18.0.

## The AMG v2 fix

AlgebraicMultigrid v2 changed the default coarse solver from `Pinv` to a sparse QR solver. QR's solve is not a symmetric operator, so `Krylov.cg` rejects the resulting preconditioner and every raster pairwise run fails outright:

```
ERROR: The linear operator `A` or the preconditioner `M` is not symmetric positive definite.
```

Passing `coarse_solver = AlgebraicMultigrid.Pinv` explicitly at both `smoothed_aggregation` call sites (`src/core.jl`, `src/raster/advanced.jl`) restores exactly the v1 behavior.

That is also the right choice for the threaded path: `solve` in `core.jl` deep-copies the multilevel workspace per task but *shares* `ml.coarse_solver`. `Pinv` applies a precomputed matrix via `mul!`, whereas a shared SPQR factorization would not be safe to reuse that way.

The rest of the v1 → v2 surface Circuitscape depends on is unchanged:
- the `MultiLevel` constructor signature still matches the per-task reconstruction in `core.jl`,
- `aspreconditioner` is untouched,
- the default `GaussSeidel`/`SymmetricSweep` smoother — now stored per-`Level` and shared across threads — is stateless (`FastGSSmoother` holds only `A`, `sweep`, `iter`), so sharing `ml.levels` remains safe.

## Test plan

Full suite with `JULIA_NUM_THREADS=4`, all passing:

```
Unit tests                 |  17    17
CG+AMG, parallel, Float64  | 719   719
CHOLMOD, parallel, Float64 | 719   719
Issue 341: included pairs  |  24    24
```

⚠️ The Accelerate and Pardiso suites were **skipped** locally, so the `AppleAccelerate` 0.7 bump is not covered by a run. `AppleAccelerate` is a weakdep and is not in `[extras]`/`targets`, so `runtests.jl`'s `@eval using AppleAccelerate` fails and silently skips — this is pre-existing and not caused by these bumps, but it does mean CI does not exercise that extension. Worth a follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ede3998f2a8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.