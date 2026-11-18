# Issue

**Title:** Impute only numeric variables by default in knn_impute

## Description

`ep.pp.knn_impute` now imputes all numeric variables when `var_names` is `None` instead of selecting every variable and raising "Can only impute numerical data". This makes the default work after `ep.pp.encode(autodetect=True)`, for example on MIMIC-II.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf31015a0972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.