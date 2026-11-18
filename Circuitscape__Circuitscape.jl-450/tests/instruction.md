# Issue

**Title:** Test improvements, IO thread safety, and CI refactor

## Description

## Summary

Test suite refactor, thread-safe file I/O, and CI improvements.

## Changes

- **Test refactor**: `compute_with(str; solver, precision, parallel)` and `runtests(; solver, precision, parallel)` replace the old function-based dispatch
- **Full parallel test suites**: CG+AMG and CHOLMOD both run the full 719-test suite in parallel
- **IO_LOCK**: Serialize ArchGDAL/file writes from parallel threads (GDAL C library is not thread-safe)
- **Test cleanup**: `clean_output()` at start and end of test runs; `test/output/` in `.gitignore`
- **CI**: ubuntu runs full suite + Pardiso; windows + macOS run full suite
- **Bug fix**: Guard `d[(pi,pj)]` lookup with `haskey` for included pairs edge case

## Thread safety

- AMG preconditioner: hierarchy shared (read-only), workspace `deepcopy`'d per task
- Cumulative map accumulation: protected by `CUM_LOCK`
- File I/O (ArchGDAL, writedlm): protected by `IO_LOCK`

## Known issue

Intermittent test failure on Windows CI in parallel CG+AMG (~1 in 3 runs). Large residual suggests corrupted solver state. Cannot reproduce locally. All shared state is either read-only or per-task via deepcopy.  for investigation.

## Test suite (1479 tests)

| Test set | Tests | Solver | Threading |
|----------|-------|--------|-----------|
| Unit tests | 17 | — | — |
| CG+AMG, parallel, Float64 | 719 | CG+AMG | parallel |
| CHOLMOD, parallel, Float64 | 719 | CHOLMOD | parallel |
| Pardiso, parallel, Float64 | 719 | Pardiso | parallel (CI only) |
| Issue 341: included pairs | 24 | CG+AMG | sequential |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `321b322155ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.