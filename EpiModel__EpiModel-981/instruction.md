# Issue

**Title:** Fix saveout.net to preserve NULL values across simulations

## Description

## Summary

- Fixes `saveout.net` to correctly store `NULL` values when saving simulation outputs across multiple runs
- Replaces all `out[[name]][[s]] <- value` assignments with NULL-safe `list()` wrapping patterns

## Motivation

In R, `mylist[[i]] <- NULL` silently *removes* the element rather than storing it. In `saveout.net`, the pattern `out[[el.name]][[s]] <- dat[[el.name]]` was used throughout to store per-simulation results. If any simulation produced a `NULL` value for a saved element (e.g., via `save.other`, `attr.history`, `raw.records`, or `diss.stats`), that simulation's slot would be silently dropped from the output list, shifting all subsequent indices and causing misalignment between simulation numbers and their stored data.

The fix uses two idiomatic R patterns:
- **s == 1 (initialization):** `out$x <- list(val)` instead of `out$x <- list(); out$x[[1]] <- val`
- **s > 1 (append):** `out$x <- c(out$x, list(val))` instead of `out$x[[s]] <- val`

Both preserve `NULL` as an explicit list element (`list(NULL)`) rather than letting it delete the entry.

## Test plan

- [x] `R CMD check` passes (CI)
- [x] Multi-simulation netsim runs produce correctly indexed output (same number of list elements as `nsims`)
- [x] Elements that can be `NULL` (e.g., `save.other` referencing a missing element, `diss.stats` for non-edgesonly models) are preserved as `NULL` entries rather than dropped

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7dbcbedf5fe5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.