# Issue

**Title:** Avoid rebuilding notebooks and documentation if dependencies did not change

## Description

(no description provided in source PR)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29257702f0d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.