# Issue

**Title:** downgrade xgboost

## Description

Downgrade xgboost to version 1.7.7.1 to solve #803 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a417653af321`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.