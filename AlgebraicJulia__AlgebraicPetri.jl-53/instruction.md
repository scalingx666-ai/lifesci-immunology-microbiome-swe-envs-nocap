# Issue

**Title:** Added github action to automate rebases on PRs

## Description

Commenting on a PR with "/rebase" will trigger the bot to automatically update the PR with the master branch using a rebase. This will help us not use the "merge master into X" button on GitHub which pollutes the commit log with unnecessary commits that don't add any content.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `992fba2ce960`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.