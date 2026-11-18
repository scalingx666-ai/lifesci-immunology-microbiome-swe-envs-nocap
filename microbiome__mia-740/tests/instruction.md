# Issue

**Title:** Adding difference and division

## Description

This pull request adds now two new transformations to the transformAssay() function: difference (computes all pairwise differences (x - y) between features (rows) across samples) and division (computes all pairwise ratios (x / y) between features)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dde1d582940f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.