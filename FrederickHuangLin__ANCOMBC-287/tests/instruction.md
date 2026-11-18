# Issue

**Title:** Correct passing of arguments to Winsorize.

## Description

In sparse_linear and sparse_dist, DescTools::Winsorize is now called with` quantile(x, probs = wins_quant, na.rm = TRUE)`. This should resolve #278.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e97abeaf1896`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.