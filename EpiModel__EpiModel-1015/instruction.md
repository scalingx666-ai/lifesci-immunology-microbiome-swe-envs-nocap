# Issue

**Title:** Clarify module.order/resimulate.network interaction, warn on tergmLite override

## Description

## Summary

.

The original issue reported that `resimulate.network = TRUE` overrides `module.order`. Investigation of the current codebase shows this is not the case — `module.order` is always respected regardless of `resimulate.network`. The `resimulate.network` flag only controls whether `resim_nets.FUN` performs actual network resimulation, not the order in which modules execute.

This PR addresses all three actionable items from the issue:

1. **Documentation** — Updated roxygen docs for `resimulate.network`, `tergmLite`, and `module.order` in `control.net()` to clarify their interactions and the default module execution order
2. **`message()` → `warning()`** — The `tergmLite = TRUE` override of `resimulate.network` now uses `warning()` instead of `message()`, so the override is visible in `.Rout` logs and captured by `tryCatch(warnings = ...)`
3. **Tests** — Added tests verifying that `module.order` is preserved with both `resimulate.network = TRUE` and `FALSE`, and that the `tergmLite` override produces a warning

## Test plan

- [x] `R CMD check` passes
- [x] `testthat::test_file("tests/testthat/test-newmodules.R")` — all 60 tests pass
- [x] `tergmLite = TRUE` with `resimulate.network = FALSE` now produces a warning instead of a message

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c69130c0528`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.