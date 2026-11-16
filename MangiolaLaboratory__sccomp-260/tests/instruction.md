# Issue

**Title:** Fix prec_coeff bug in glm_multi_beta_binomial.stan

## Description

Fix minor bug that prec_coeff's prior is set twice in the model. Not likely to cause real problems for any dataset large enough, but for sanity it should be corrected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0095fc7e8036`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.