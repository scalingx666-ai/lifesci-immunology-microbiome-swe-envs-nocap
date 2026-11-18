# Issue

**Title:** Make LAPACK and BLAS libraries available to user code

## Description

Make LAPACK and BLAS libraries available when using BioDynaMo. Both are already used when building BioDynaMo for the multi-simulation runtime.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21051b24b5d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.