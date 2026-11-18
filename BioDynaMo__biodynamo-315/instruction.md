# Issue

**Title:** Fix notebooks on Ubuntu

## Description

Fix notebook dependencies on Ubuntu. The Jupyter environment is fragile when it comes to small changes in the pip dependencies. This PR fixes all Jupyter related packages to a specific version such that the notebooks work and (hopefully) keep working.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4573aa62f444`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.