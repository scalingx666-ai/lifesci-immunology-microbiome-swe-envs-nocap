# Issue

**Title:** Let `k` in `test_kj` be a covariate name

## Description

`k` can either be numeric, a string that matches a column name of `X`, or a string that starts one or more column names of `X` (this last case corresponds to a formula like `~ Group` where `Group` has values in `c("A", "B", "C")`, and then will test all covariates of the form `GroupB`, `GroupC`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0f8b76f2518`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.