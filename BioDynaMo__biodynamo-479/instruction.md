# Issue

**Title:** Run repository-check workflow on pull requests

## Description

The code-style job (clang-format and copyright checks) only triggered on push, so external contributors' PRs never ran it until after merge to master.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9dc6dd13ab31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.