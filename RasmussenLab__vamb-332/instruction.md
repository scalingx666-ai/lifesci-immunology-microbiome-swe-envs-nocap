# Issue

**Title:** Switch Black formatter to Ruff

## Description

This lets us use the same tool for both linting and formatting, simplifying things. Also, Ruff is faster, and installs with no dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dea001f61bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.