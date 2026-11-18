# Issue

**Title:** Fixed misleading error message for -l/-p

## Description

Error message when -p and -l are both used was wrong (and confusing). This fixes it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11fea1b6aae0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.