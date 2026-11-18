# Issue

**Title:** Replace GitHub Action tool to work

## Description

## Related issues
Close #1754

## What was changed
Replace GitHub Action tool to work.

## Summary by Sourcery

Update the GitHub Actions workflow to use 'conda-incubator/setup-miniconda' for setting up conda, replacing the previous 's-weigand/setup-conda' action.

CI:
- Replace the GitHub Action for setting up conda from 's-weigand/setup-conda' to 'conda-incubator/setup-miniconda' in the test workflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfc3d6693701`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.