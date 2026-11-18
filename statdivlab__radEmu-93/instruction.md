# Issue

**Title:** Checking rank of design matrix in emuFit_micro

## Description

Check added to function emuFit_micro to ensure design matrix inputted to the function is full-rank. If the matrix is not, an error message is printed, explaining what the problem is and suggesting ways to address it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be6a51b7091b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.