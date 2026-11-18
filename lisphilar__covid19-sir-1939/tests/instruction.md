# Issue

**Title:** test: ignore numpy timedelta generic unit deprecation warning

## Description

Add an ignore filter to pyproject.toml to suppress the `DeprecationWarning` regarding the generic unit for NumPy timedelta. This resolves the failing `test_forecast` in `test_ml.py` as pytest was configured to treat warnings as errors.

---
*PR created automatically by Jules for task [8626908885939323562](https://jules.google.com/task/8626908885939323562) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3c07e1ac982`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.