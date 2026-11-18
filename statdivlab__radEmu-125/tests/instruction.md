# Issue

**Title:** Add helper function to make constraint function and gradient functions when using reference taxon constraint

## Description

Make helper function, add tests, and add this function to vignette. In vignette, say that we recommend using the "typical" log fold-difference constraint for the intercept and a reference taxon for the covariates. 

@adw96 I won't merge this quite yet, in case you want to quickly look over the update in the vignette to see if there's anything you would change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a95e6de4313`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.