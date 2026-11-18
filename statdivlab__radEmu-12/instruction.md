# Issue

**Title:** Update emuFit so that when use_both_cov = TRUE, I_inv rather than jus…

## Description

Proposed update to emuFit.R so that I_inv is fed to get_score_stat (rather than just_wald_things$I) for computation of robust score stat using full model information matrix when use_both_cov = TRUE. Pull request in response to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01ef6c2e947f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.