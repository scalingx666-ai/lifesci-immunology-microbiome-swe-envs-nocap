# Issue

**Title:** Update codecov script to target dev branch

## Description

We must re-target the branch on codecov for `dev`, otherwise we will not get reports when PRs are targeting `dev`.

This should be merged before #76 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4dd6a5a6ded`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.