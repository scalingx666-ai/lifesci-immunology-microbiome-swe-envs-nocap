# Issue

**Title:** Allow character grouping columns in factor smooths

## Description

`mgcv` factor smooths (`bs = "fs"`) require grouping variables to be factors, but character columns caused smooth construction errors.

- **Internal coercion:** Convert character variables used by `bs = "fs"` smooth terms to factors before calling `mgcv::smoothCon()`.
- **Regression coverage:** Add a unit test for character grouping input.

```r
data <- data.frame(
  x = seq(0, 6, length.out = 24),
  tissue = rep(c("blood", "lymph", "tumor"), length.out = 24)
)

parse_formula_smooths(~ s(x, tissue, bs = "fs", k = 5), data)
```

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99257304418f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.