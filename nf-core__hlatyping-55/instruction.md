# Issue

**Title:** PR for 1.1.4

## Description

This should address:

- centralized configs issues
- pinning numpy to 1.15.4 to fix pandas issues with OptiType

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18740c24175e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.