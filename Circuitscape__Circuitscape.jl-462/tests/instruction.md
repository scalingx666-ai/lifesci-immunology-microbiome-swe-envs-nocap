# Issue

**Title:** Robustness and code cleanup

## Description

## Summary
- Rename `laplacian()` to `laplacian!()` to follow Julia convention for mutating functions
- Add error branch to `get_solver()` for unknown solver types (previously returned `nothing`)
- Replace `something(findfirst(...), 0)` with explicit `nothing` checks that throw clear errors when nodes are not found in components
- Replace `@assert` in all `solve_linear_system` methods with explicit `error()` calls so solver convergence failures are never silently ignored (assertions can be disabled at runtime)
- Make `_open()` case-insensitive for `.gz`/`.GZ` file detection
- Remove dead code: `__precompile__` comment, unused `MutablePair` struct, commented-out `laplacian`/`findin` calls, unused `pair_numbers` in CHOLMOD path
- Replace magic number `-777` with named constant `RESISTANCE_INVALID`
- Deduplicate `compute(path)` and `compute(dict)` via shared `_run()` helper
- Simplify `get_output_flags` to direct constructor call

## Test plan
- [x] Full test suite passes locally with 4 threads (Unit: 17, CG+AMG: 719, CHOLMOD: 719, Issue 341: 24)
- [x] CI passes on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `616d6343456c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.