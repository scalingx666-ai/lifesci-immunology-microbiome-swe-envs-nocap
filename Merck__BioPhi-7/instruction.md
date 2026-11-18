# Issue

**Title:** Shift Conda channels from Dockerfile to environment.yml

## Description

This PR shifts Conda channels from `Dockerfile` to `environment.yml`.

This enables building the Conda environment outside of Docker.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc76b077418d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.