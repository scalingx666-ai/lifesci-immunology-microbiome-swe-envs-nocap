# Issue

**Title:** Write medoid to cluster metadata file

## Description

It's often useful to know which medoid was used to generate a cluster. Remarkably, we didn't think to output it earlier.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3828e3dcc411`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.