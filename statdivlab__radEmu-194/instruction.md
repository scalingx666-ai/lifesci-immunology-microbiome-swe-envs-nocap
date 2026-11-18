# Issue

**Title:** Return instead of crashing when fit_null throws on every try

## Description

If fit_null() threw on all ntries attempts, score_test() left the retry loop with constrained_fit still a try-error. It then crashed on constrained_fit$B ("$ operator is invalid for atomic vectors"), which aborted the whole emuFit() call and lost every other test's result.

score_test() now checks for a try-error after the retry loop. If it finds one, it warns with the underlying error message and returns NULL. emuFit() already skips a NULL result, so that test's score_stat and pval stay NA. It also sets the test's converged to "failed with error", so the test is listed in null_estimation_unconverged.

Add tests that mock fit_null() to always error and check that score_test() warns and returns NULL, and that emuFit() reports NA and marks the tests as failed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb2d6c596358`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.