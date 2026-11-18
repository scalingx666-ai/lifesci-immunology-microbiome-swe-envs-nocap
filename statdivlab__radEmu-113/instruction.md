# Issue

**Title:** add function `make_design_matrix()`

## Description

add function `make_design_matrix()` as a wrapper for `stats::model.matrix()` considering different potential data inputs, to create a design matrix from data and a formula. This can be used by the user to determine covariate indices k in the argument `test_kj` if they do not know them (this would be useful for more complex models with factors). Update the documentation of `emuFit()` for argument `test_kj` to point users to this function if they need it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0838e5a05641`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.