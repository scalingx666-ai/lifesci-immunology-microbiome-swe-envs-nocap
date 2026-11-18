# Issue

**Title:** Unifre mount issue with docker.

## Description

The code was only using the singularity --bind flag, instead of checking the container engine used.

Now it supports docker -v for unifire, as it's done for IPS.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91bece916c01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.