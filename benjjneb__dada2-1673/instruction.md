# Issue

**Title:** Update plot-method.R for ggplot2 compatibility

## Description

`size` ->  `linewidth`
guides(fill=FALSE) -> guides(fill="none")

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6fd6d28a07e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.