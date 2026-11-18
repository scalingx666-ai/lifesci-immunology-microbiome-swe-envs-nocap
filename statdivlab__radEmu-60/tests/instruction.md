# Issue

**Title:** Return information about optimization under the null (for running score tests).

## Description

Add in object `score_test_hyperparams` that is returned when score tests are run and includes `u`, `rho`, `tau`, `inner_maxit`, `gap`, and `convergence` for each score test that is run.

This addresses issue #59, because you could run a small subset of score tests, see the final values of `tau` and `inner_maxit` (if they are changed during the course of optimization), and use these to set hyperparameters for the entire set of score tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3feca52e639b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.