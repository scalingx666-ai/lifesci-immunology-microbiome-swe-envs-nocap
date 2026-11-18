# Issue

**Title:** Add Apple Accelerate sparse solver backend

## Description

## Summary
- Adds Apple's Accelerate framework sparse Cholesky solver as a new solver backend via `AppleAccelerate.jl` (weak dependency / package extension)
- Users can select it with `solver = accelerate` in their INI config file
- Follows the same extension pattern as the existing Pardiso solver — supports batched solves with residual checking

## Changes
- `ext/CircuitscapeAppleAccelerateExt.jl` — new extension implementing `construct_cholesky_factor` and `solve_linear_system` for `AAFactorization`
- `src/core.jl` — new `AccelerateSolver <: Solver` type, added to direct solver dispatch union
- `src/config.jl` — `st_accelerate` enum value, parsing and serialization
- `src/consts.jl` — `ACCELERATE` string constant for config parsing
- `src/raster/advanced.jl` — `multiple_solve` method for `AccelerateSolver`
- `Project.toml` — weak dependency and compat entry for `AppleAccelerate = "0.6"`
- `test/runtests.jl` — runs full test suite with Accelerate solver when available (macOS)

## Test plan
- [x] All 719 tests pass with `solver="accelerate"` (sequential)
- [x] All 719 tests pass with `solver="accelerate"` (parallel, 4 threads)
- [x] All 719 tests pass with `solver="cg+amg"` (no regression)
- [x] All 719 tests pass with `solver="cholmod"` (no regression)
- [x] CI will skip Accelerate tests on Linux (graceful fallback via try/catch)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2971b7100416`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.