# Issue

**Title:** update behavior of `emuFit()` related to `refit = TRUE`

## Description

update behavior of `emuFit()` so that if `refit = TRUE` and either `B` or `fitted_model` is non-null, then the `B` provided is used as a starting point for refitting the model

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc325c255d64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.