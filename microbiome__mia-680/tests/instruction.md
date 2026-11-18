# Issue

**Title:** Handle duplicates in getDivergence

## Description

The function now handles cases where single sample has multiple reference samples. Related to this:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `255ac6854cd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.