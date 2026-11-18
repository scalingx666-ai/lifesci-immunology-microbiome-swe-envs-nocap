# Issue

**Title:** Fixes mean.lwd issue

## Description

## Summary

Fixes a bug in `plot_netsim_epi()` where dead-code `is.null` branches for `mean.lwd` and `mean.lty` used inconsistent default values between the y-axis range calculation phase and the actual drawing phase (1.5 vs 2.5 for `mean.lwd`). In practice, the first branch always won, making the second branch dead code — but the inconsistency was confusing and masked the intended behavior.

This PR removes the dead `is.null` branches entirely, since the function signature already provides sensible defaults (`mean.lwd = 2`, `mean.lty = 1`). The redundant `!is.null` guard on the `length()` checks is also removed, as `length()` works correctly on non-NULL values from the function signature.

The same cleanup is applied to `mean.lty`, which had a similar dead-code pattern.

## Changes

- **`R/plot.netsim.R`**: Removed dead `is.null(mean.lwd)` and `is.null(mean.lty)` branches in both the y-axis calculation block and the drawing block. Simplified the remaining `length()` recycling guards.
- **`NEWS.md`**: Added bug fix entry.

## Test plan

- [x] Verify `plot(netsim_result)` renders correctly with default arguments
- [x] Verify explicit `mean.lwd` and `mean.lty` values are respected
- [x] Verify multi-compartment plots correctly recycle `mean.lwd`/`mean.lty` when fewer values than compartments are provided
- [x] `R CMD check` passes

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9070ece84b62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.