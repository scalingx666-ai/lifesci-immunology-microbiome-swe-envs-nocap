# Issue

**Title:** Winsorize and clip all numeric variables without var_names

## Description

ep.pp.winsorize and ep.pp.clip_quantile without var_names and obs_cols now apply to all numeric variables, like the normalization functions, instead of silently changing nothing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5273b1b72a6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.