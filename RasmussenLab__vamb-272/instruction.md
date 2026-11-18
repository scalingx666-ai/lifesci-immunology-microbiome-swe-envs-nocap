# Issue

**Title:** Add Ruff linting to CI

## Description

This check catches quite a few bugs and code quality issues. It's very fast to run locally, so shouldn't be too much a pain in the ass. Ruff is configured through pyproject.toml.
We can always disable this check if it becomes too annoying

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `583fe2666d39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.