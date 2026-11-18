# Issue

**Title:** Remove dead fields and fix type instabilities

## Description

## Summary
- Remove unused `solver::String` field from `RasterFlags` and `NetworkFlags` — the field was set via `_solver_str()` but never read; solver dispatch uses `cfg.solver` (enum) and `prob.solver` (typed struct) instead
- Remove untyped dead field `A` from `PardisoFactorize` — it was written (`p.A = A`) but never read
- Mark `ps` and `verbose` as `const` in `PardisoFactorize` since they are never mutated after construction

## Test plan
- [x] Full test suite passes locally (Unit tests: 17, CG+AMG: 719, CHOLMOD: 719, Issue 341: 24)
- [x] CI passes on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c31a8409c60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.