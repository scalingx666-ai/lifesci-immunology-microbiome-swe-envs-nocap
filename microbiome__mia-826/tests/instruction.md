# Issue

**Title:** Fixed PC explained vars in joint-RPCA

## Description

This fixes the discrepancy in expained variance w.r.t. Gemelli.

The reason was the sorting of svd values (descending vs. ascending); this had been noted elsewhere in the code but was left undone on line 728 of R/getRPCA.R

Now the explained variances match between mia ("percentVar") and Gemelli.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78047df22a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.