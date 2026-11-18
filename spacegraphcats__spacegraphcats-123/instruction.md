# Issue

**Title:** refactor minhashes.db writing so that it is cleaner and lower-memory

## Description

This PR should not change any file formats.

note that this fixes leveldb so that it actually does use batch writing ;).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b0c01177d44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.