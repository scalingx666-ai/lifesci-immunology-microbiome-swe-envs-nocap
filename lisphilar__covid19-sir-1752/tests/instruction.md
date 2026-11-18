# Issue

**Title:** use the latest versions of GitHub Actions for workflows

## Description

## Related issues
Close #1751

## What was changed
Use the latest versions of GitHub Actions for workflows.

## Summary by Sourcery

Update GitHub Actions workflows to use the latest versions of actions by removing specific version tags, ensuring that the workflows always use the most recent stable releases.

CI:
- Update GitHub Actions workflows to use the latest versions of actions by removing specific version tags.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbb92892e34e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.