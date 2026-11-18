# Issue

**Title:** Skip rarely observed predictors in gradient_boosting_impute

## Description

ep.pp.gradient_boosting_impute leaves out predictors observed in fewer rows than a leaf needs, so it no longer crashes when the few values of a rarely measured variable all fall into the early-stopping validation split, and it warns for variables that stay missing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8d0c2234605`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.