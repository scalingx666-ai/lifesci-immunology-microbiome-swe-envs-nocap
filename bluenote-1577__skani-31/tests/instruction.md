# Issue

**Title:** Fix output format in triangle mode

## Description

In triangle mode, when an output file is provided, skani  generates:
1. A lower triangular matrix without a diagonal by default
2. A lower triangular matrix with a diagonal when --full-matrix is provided

IMO, the correct behaviour should be:
1. A lower triangular matrix with a diagonal by default
2. A full matrix when --full-matrix is provided

What do you think?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee3132a4bf00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.