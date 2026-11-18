# Issue

**Title:** Switch CI to Ubuntu 24.04

## Description

This aligns Linux build, workflow test, Docker build, and release jobs on the newer GitHub runner image.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07ae1e828af9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.