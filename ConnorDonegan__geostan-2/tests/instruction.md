# Issue

**Title:** Compatibility with Future RStan

## Description

This PR contains some minor changes to make your package compatible with the upcoming RStan 2.26. I've removed the `src` folder and `stanmodels.R` file, as these are fully handled by `rstantools`.

I've also made a small change to the `model.stan` file, where the `rep_vector(mu_x_true[j], n)` argument is first assigned to a temporary vector before being passed to the `auto_normal_lpdf` likelihood. This is due to some transition issues when using the older `rstan` with the newer `StanHeaders`, and can be reverted once the newer versions of both are on CRAN.

Feel free to let me know if you had any questions!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20500841883a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.