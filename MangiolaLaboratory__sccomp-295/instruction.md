# Issue

**Title:** Report informative errors for NA input columns

## Description

NA values in `sample` or formula factor columns triggered an unrelated `object 'columns' not found` error during validation.

- **Validation:** derive selected column names before checking for missing values.
- **Regression coverage:** verify informative errors for NA values in both `sample` and formula factor columns.

```r
# Now reports the offending columns
"There are NA values in your tibble for any of the column sample, cell_group, type"
```

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99257304418f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.