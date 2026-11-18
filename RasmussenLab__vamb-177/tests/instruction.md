# Issue

**Title:** Bump Cython compat version

## Description

ABI changes in Python 3.11 is incompatible with Cython versions < 0.29.5. This may fix #176, or may not.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca907e2668a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.