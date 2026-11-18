# Issue

**Title:** BLD: General updates to the repository

## Description

- Updates the setup.py file to no longer use distutils.
- Improves the long_description section to load the README.md file.
- Adds publications to the README.md file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `097b6542fa7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.