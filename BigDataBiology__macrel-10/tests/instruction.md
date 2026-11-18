# Issue

**Title:** ENH More robust setup

## Description

- Before, it would install miniconda, but assume that the user would
install to the default location.
- Do not change any global conda settings.
- Do not change permissions on all python files, just the expected ones

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16c962084f76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.