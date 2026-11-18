# Issue

**Title:** better delimiter

## Description

changed internal delimiter for multi-hit reads to '••' to prevent clashes with user defined read names

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cb6eedbecb7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.