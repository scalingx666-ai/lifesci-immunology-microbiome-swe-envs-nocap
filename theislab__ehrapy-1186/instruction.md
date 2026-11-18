# Issue

**Title:** Standardize covariates in the logistic propensity model

## Description

The logistic propensity model of the causal estimators and diagnostics standardizes the covariates before fitting, so that estimates no longer depend on covariate units and the fit converges on unscaled covariates instead of raising ConvergenceWarnings and destabilizing matching.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `701cebd471d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.