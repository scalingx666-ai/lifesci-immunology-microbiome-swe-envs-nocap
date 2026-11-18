# Issue

**Title:** Cross-fit the nuisance models of aipw

## Description

`ep.tl.aipw` cross-fits its propensity and outcome models over `n_folds` treatment-stratified folds, so that its standard error stays valid for flexible models such as gradient boosting instead of collapsing (0.010 in-sample against 0.048 cross-fitted on MIMIC-II).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `242e57b18bc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.