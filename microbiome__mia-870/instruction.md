# Issue

**Title:** Add getPCA and addPCA

## Description

Adds getPCA and addPCA, wrappers for scater::calculatePCA that use all features by default, as suggested in microbiome/OMA#883.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01119c34d1a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.