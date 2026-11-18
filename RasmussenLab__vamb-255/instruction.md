# Issue

**Title:** Validate arguments to ReclusteringOptions

## Description

This allows Vamb to fail early if passed paths to files that do not exist.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d044c97a047`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.