# Issue

**Title:** Build survival and regression model inputs from obs and variables

## Description

Survival fitters, `ols`, `glm` and `cox_ph_adjusted_curves` now take durations, events, strata and covariates from `edata.obs` or variables and only drop observations missing a column the model actually uses.
Before, every patient with a missing value in any variable was silently excluded, even from models that never used that variable, and outcomes stored in `obs` could not be used at all.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ef2ba54dbdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.