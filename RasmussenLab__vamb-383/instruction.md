# Issue

**Title:** Fix Ruff linting CI

## Description

For some reason the old one didn't work, and didn't alert us to the fact that it didn't.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77e1cba32a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.