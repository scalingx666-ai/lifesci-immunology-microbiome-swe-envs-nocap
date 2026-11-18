# Issue

**Title:** Bugfix/transpose on detect output

## Description

If there is only one category of viruses detected - it should be converted to List anyway

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1797677183bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.