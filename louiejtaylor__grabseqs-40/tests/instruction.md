# Issue

**Title:** Gracefully handle missing dependencies

## Description

This PR adds more graceful handling of missing dependencies, adds tests for these cases, and generalizes file compression to a function in `utils` which handles multiple compression options (notably `pigz` for multithreading, and `gzip` as a reasonable baseline). This PR will close #36.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2e97828bf3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.