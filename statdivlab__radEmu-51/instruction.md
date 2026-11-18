# Issue

**Title:** Addressing issue from data from Amy's email

## Description

Addressing issue from data from Amy's email, which was due to the information matrix being computationally singular for one score test in the analysis being run. I put the call to `get_score_stat` within a try block, and add a warning if there is an error. 

I additionally made a few small updates to `emuFit` that came up while I was working on this, to make sure that coefficients table is correctly output (before there was an error when running an analysis with `compute_cis = FALSE` and `return_both_score_pvals = TRUE`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26dc3354dafa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.