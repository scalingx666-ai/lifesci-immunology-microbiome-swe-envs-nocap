# Issue

**Title:** Enhance NA handling in complex interaction design matrix

## Description

- Bump package version in DESCRIPTION file.
- Introduce `calculate_na_fraction_contribution` function to compute contributions of NA values in design matrices.
- Add `handle_missing_values` function to standardize NA handling for categorical and numeric variables.
- Update NAMESPACE to export new functions and import necessary dependencies.
- Add documentation for new functions and enhance existing tests to cover NA scenarios in design matrices.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d69bc89cbe2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.