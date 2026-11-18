# Issue

**Title:** Remove name attribute from Chemotaxis and Secretion classes

## Description

Reduce memory footprint, by removing these unused attributes.
The name can be obtained from the diffusion grid.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ae4e5df6b5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.