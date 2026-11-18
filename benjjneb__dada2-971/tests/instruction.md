# Issue

**Title:** Fix double "y" scale warning for plotQualityProfile()

## Description

To prevent the below error message when using `plotQualityProfile()`

> Scale for 'y' is already present. Adding another scale for 'y', which will replace the existing scale.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `963f4e023023`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.