# Issue

**Title:** feat(ci): add dependabot

## Description

Adds dependabot to keep GitHub actions up-to-date.

You can enable it following these instructions: https://docs.github.com/en/code-security/tutorials/secure-your-dependencies/dependabot-quickstart#enabling-dependabot-for-your-repository.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79c94b838aca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.