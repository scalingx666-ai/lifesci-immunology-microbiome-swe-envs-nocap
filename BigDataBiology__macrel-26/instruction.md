# Issue

**Title:** Fixed building in Travis

## Description

- Fixing R version in the install.sh script to avoid conflict during peptides R package installation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb00f55370d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.