# Issue

**Title:** Make formula parsing more robust

## Description

Currently,  `formula = x ~ diagnosis + `Age at diagnosis`` will fail as there are backticks. This PR will fix the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7072b981515`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.