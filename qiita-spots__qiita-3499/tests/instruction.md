# Issue

**Title:** Expand identifier set

## Description

Replaces #3498 

This pull request introduces sample_idx, prep_sample_idx and artifact_sample_idx values. These are Qiita-wide unique and provide an integer identifier for use within study, prep and artifact respectively.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74ad1ba972f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.