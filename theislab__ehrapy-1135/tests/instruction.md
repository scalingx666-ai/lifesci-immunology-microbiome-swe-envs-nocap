# Issue

**Title:** Add gradient_boosting_impute

## Description

.
Adds `ep.pp.gradient_boosting_impute`, which imputes every variable with a gradient boosting model trained under the missingness it is applied to and, for longitudinal data, also uses the closest observed values in time, and makes `miss_forest_impute` keep one forest in memory instead of all of them.
With every variable held out at 10% of the observed hours of all 11,988 PhysioNet 2012 patients, its RMSE on standardized values is 0.62 in 36 seconds, against 0.82 for LOCF and 1.09 in 232 seconds for MissForest.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `409b46b04a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.