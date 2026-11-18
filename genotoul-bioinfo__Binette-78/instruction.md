# Issue

**Title:** Drop support for pyrodigal v2

## Description

Drop support for pyrodigal v2 as its performance was quite bad compared to v3. 
Also cached conda env in the CI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `370a26422580`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.