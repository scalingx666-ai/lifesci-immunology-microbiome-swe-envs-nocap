# Issue

**Title:** Bump the tutorials to the cohort tutorial

## Description

Adds the new cohort tutorial to the docs in place of cohort_tracking and imputation_nb and drops the tutorials removed in ehrapy-tutorials#76, with redirects for all old URLs. It also fixes the missing longitudinal thumbnail and gives the prediction tutorial one.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e46aa6e93f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.