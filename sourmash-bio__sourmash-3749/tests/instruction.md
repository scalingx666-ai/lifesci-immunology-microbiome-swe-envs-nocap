# Issue

**Title:** ci: group dependabot updates by language

## Description

Use [dependabot dep groups](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#groups--) to limit the number of PRs (and rebuilds) when updating dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c94f1438c442`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.