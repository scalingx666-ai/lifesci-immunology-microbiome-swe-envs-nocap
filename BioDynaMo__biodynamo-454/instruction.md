# Issue

**Title:** ci: fix script download 404 on PRs from forks

## Description

Update GHA_REPOSITORY to use GitHub context variables. This ensures that scripts are fetched from the correct head repository and branch during Pull Request events, preventing fetching a wrong URL.

This

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8aa228052ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.