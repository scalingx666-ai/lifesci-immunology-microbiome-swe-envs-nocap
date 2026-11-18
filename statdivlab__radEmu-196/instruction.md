# Issue

**Title:** Report failed discrete null fits as not converged

## Description

fit_null_discrete_micro_fs can exit early when the ridge solve or line search fails. Both of these set `final_iter <- iter - 1`, so fit_null_discrete's `iter < maxit` check treated them as converged, and score_test used this. fit_null_discrete_micro_fs now returns `failed = TRUE` for these exits, and fit_null_discrete checks this flag in addition to the `iter < maxit check` when determining convergence, which handles these cases.

Also, needed to raise the testthat minimum in Suggests to 3.1.7 for the mocking functions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4af18e6d4ef4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.