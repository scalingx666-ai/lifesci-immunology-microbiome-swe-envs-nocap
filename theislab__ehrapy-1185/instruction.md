# Issue

**Title:** Treat numeric variables of object data as numeric in causal designs

## Description

The causal estimators and diagnostics convert variables of an object `X` to numbers when all their values are numeric, so that on the default `ed.dt.mimic_2()` they adjust for age and SOFA instead of one-hot encoding every distinct value (1,773 balance rows for two covariates).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf51fd095f83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.