# Issue

**Title:** ci: github actions improvements

## Description

- NPM publish uses [trusted publishers](https://docs.npmjs.com/trusted-publishers)
- limit permissions in workflows

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `25221f4ad4c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.