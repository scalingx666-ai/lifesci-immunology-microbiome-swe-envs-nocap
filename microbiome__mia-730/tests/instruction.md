# Issue

**Title:** Transform method replacing values with NA

## Description

Added method that replaces values <= threshold with NA. 

`transformAssay(tse, method = "cutoff", threshold = 0)`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b06895fc840c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.