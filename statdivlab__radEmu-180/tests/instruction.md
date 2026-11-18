# Issue

**Title:** Various updates before submitting to CRAN, including those from issue #178

## Description

Various updates before submitting to CRAN, including those from issue #178. 

- updates the description of the return object when using `?emuFit`
- adds a "quick start" vignette to give a quick example of running `emuFit()` and interpreting results
- adds `X_cup_from_X_fast()` and `get_G_for_augmentations_fast()`, two functions from PR #148 which is now pretty out of sync with the codebase
- slightly updates the information the user gets when `verbose = TRUE` 
- skips the test from `fit_null()` because this is slow and deterministic, and `fit_null()` is tested extensively in "test-fit_null_symmetric()" as the comparison method 

@adw96 right now the quick start vignette doesn't have an example for clustered data, mostly because we don't have real data with clustering and I wanted to make it as streamlined as possible. However, let me know if you want me to add one, and I can just generate fake clustering patterns for the wirbel data and fit a clustered model as an example.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82dc0ce05c5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.