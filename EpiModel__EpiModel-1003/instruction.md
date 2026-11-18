# Issue

**Title:** Update plot.netsim.R

## Description

## Summary
- Fix always-true `is.numeric(grp.flag)` condition to `grp.flag == 2`, making the warning for non-two-group networks reachable
- Remove redundant `if (!tergmLite)` guard that was always true (the `tergmLite == TRUE` case already `stop()`ed above)
- Hoist repeated `if (miss_vertex.cex) vertex.cex <- 1` out of branches into a single assignment

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c490143fddd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.