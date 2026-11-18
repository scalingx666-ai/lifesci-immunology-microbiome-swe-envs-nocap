# Issue

**Title:** avoid generating large matrix in macro_fisher_null.R

## Description

Example data from  runs slowly on macro_fisher_null() in part because a `tcrossprod(sm_half_num)` on line 74 of macro_fisher_null.R generates a large intermediate matrix that we do not have to compute.

This now fails one test (bc output of macro_fisher_null now returns the wrong information matrix). I can fix that tomorrow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3cbe567989e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.