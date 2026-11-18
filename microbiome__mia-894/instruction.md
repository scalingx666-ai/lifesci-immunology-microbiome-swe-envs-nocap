# Issue

**Title:** Add subsetBy() for stepwise filtering

## Description

Adds `subsetBy()`, a single function for filtering features and samples by conditions written as R expressions. Related to #888 (filtering functions) and #735.

```r
tse <- tse |>
    subsetBy(rows = rowSums(counts) > 10) |>
    subsetBy(rows = rowMeans(counts > 0) > 0.25) |>
    subsetBy(cols = colSums(counts) > 100000)
```

- Conditions can use assays by name (`counts`), `rowData` columns in `rows`, `colData` columns in `cols`, and variables from the calling environment (e.g. thresholds). Assays take precedence over fields with the same name.
- Each call evaluates its conditions on the object it receives, so piped steps are computed after the previous filters. This is how Gemelli filters for Joint-RPCA, unlike `filterRPCAInput()` (see ).
- `rows` is evaluated before `cols`. `NA` counts as `FALSE`. A condition of the wrong type or length gives an error.
- `collapse = TRUE` merges the features that do not meet the `rows` condition into one feature (`collapse.name = "Other"`), placed last, so sample totals stay the same. For example, the 10 most abundant features plus the rest:

  ```r
  subsetBy(tse, rows = rank(-rowMeans(counts)) <= 10, collapse = TRUE)
  ```

- Works with QC metrics stored with `addQC()`, e.g. `subsetBy(tse, rows = sd > 0 & detected >= 3, cols = total > 1e6)`. The help page notes that stored metrics are not updated after subsetting.

One general function could replace the per-metric `subsetBy*()` functions proposed in #888, and later the existing ones, through the usual deprecation cycle.

Tests: `tests/testthat/test-subsetBy.R` (29 expectations). Version 1.21.31, NEWS updated. A full `R CMD check` has not been run locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d80e7f7e659`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.