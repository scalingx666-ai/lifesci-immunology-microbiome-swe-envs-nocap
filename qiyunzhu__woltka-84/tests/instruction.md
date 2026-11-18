# Issue

**Title:** Allow users to specify cache size.

## Description

Default is 128, the recommended value for Python's LRU cache. However I suspect that higher values will work better.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61a3534d25ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.