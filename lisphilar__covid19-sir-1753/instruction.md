# Issue

**Title:** fix: errow with the `uses' attribute must be a path, a Docker image, or owner/repo@ref

## Description

## Related issues
Follow-up for #1752 

## What was changed
Fix the error with the `uses' attribute must be a path, a Docker image, or owner/repo@ref.

## Summary by Sourcery

Fix the error related to the 'uses' attribute in GitHub Actions workflows by specifying the version reference for each action, ensuring compatibility and stability in CI processes.

CI:
- Specify the version reference for GitHub Actions in the CI workflows by appending '@main' or '@master' to the 'uses' attribute in various workflow files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ee7bb3b92e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.