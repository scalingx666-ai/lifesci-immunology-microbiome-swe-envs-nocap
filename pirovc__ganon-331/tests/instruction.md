# Issue

**Title:** Bugfix/reassign batch

## Description

Fix bug #325 and additionally execute re-assignment in multiple threads for batch classification.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88b607a9bd93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.