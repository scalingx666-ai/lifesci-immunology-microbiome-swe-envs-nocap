# Issue

**Title:** Model the insert size distribution instead of taking the mean

## Description

This PR also removes the cdf code (the kde has shown to be a better way of modelling base quality overall)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12fb659d767e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.