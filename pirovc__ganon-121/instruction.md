# Issue

**Title:** Bugfix/data race map

## Description

Bugs caused on stress tests (too many LCA calls) discovered by #119

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `260dea8af0af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.