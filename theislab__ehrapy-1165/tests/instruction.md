# Issue

**Title:** Require formulaic 1.2.2 so that formulas find Q()-quoted names

## Description

`ep.tl.ols` and `ep.tl.glm` require formulaic 1.2.2, whose `required_variables` keeps names quoted as `Q('...')`, so formulas with obs columns or variables containing spaces work again. The `ep.pp.qc_metrics` docstring now names the `standard_deviation` column.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b2b6020f1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.