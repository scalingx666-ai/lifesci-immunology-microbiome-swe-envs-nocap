# Issue

**Title:** Bump deps, limit NumPy to v1

## Description

Prevents some annoying compat issues with NumPy v2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f028bdd6119c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.