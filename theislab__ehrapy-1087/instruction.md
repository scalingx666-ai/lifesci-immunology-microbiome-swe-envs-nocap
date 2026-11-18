# Issue

**Title:** Handle falsy explicit impute replacements

## Description

## Problem

`explicit_impute()` accepts mapping replacement values typed as `str | int | float`, but falsy values such as `0` are skipped because the current implementation checks replacement values by truthiness.

For example, `replacement={'intcol': 0}` should be a valid per-column replacement, but `0` is treated as if no replacement was configured.

## Fix

Use mapping key existence checks in `_extract_impute_value()` and `is not None` in the caller, so valid falsy replacements are applied. Added a regression test for `replacement={'intcol': 0}`.

## Validation

```text
.venv\Scripts\pytest.exe tests\preprocessing\test_imputation.py::test_explicit_impute_subset_accepts_falsy_replacement_value -q
# 2 passed

.venv\Scripts\pytest.exe tests\preprocessing\test_imputation.py::test_explicit_impute_subset -q
# 2 passed

python -m py_compile ehrapy\preprocessing\_imputation.py tests\preprocessing\test_imputation.py
```

## Risk

Low. This changes behavior only for mapping replacement values that are valid by type but were previously skipped because they are falsy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `041a4e8e4be3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.