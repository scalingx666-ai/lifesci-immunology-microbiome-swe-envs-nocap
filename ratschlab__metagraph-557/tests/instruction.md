# Issue

**Title:** Don't use range-based loops with omp

## Description

omp parallelization may not work with range-based loops, so always use the simple form

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cdb9874b179`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.