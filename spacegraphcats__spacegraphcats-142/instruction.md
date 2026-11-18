# Issue

**Title:** Minor

## Description

Change domgraph construction to be a shallow minor rather than to add edges based on overlap between optimal domination.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b0c01177d44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.