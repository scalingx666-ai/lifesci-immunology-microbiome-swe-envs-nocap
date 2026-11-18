# Issue

**Title:** add update to re-order covariate data if it has different rownames than response data

## Description

- add message and fix in `emuFit` when `Y` and `X` have differing row names 
- add test for this functionality

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f80a15a55f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.