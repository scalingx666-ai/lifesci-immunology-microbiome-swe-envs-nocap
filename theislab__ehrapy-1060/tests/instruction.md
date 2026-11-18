# Issue

**Title:** sparse array support for  `_warn_imputation_threshold`

## Description

`_warn_imputation_threshold` is calling `qc_metrics` to compute missing value percentages, which does not support sparse arrays

- Refactored _warn_imputation_threshold: a sparse aware path that computes missing value percentages directly using `np.isnan` on the stored values assuming missing values are explicitly stored as NaN in the sparse structure as well
- Extended test_warning() to cover sparse arrays

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fc269d2a5d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.