# Issue

**Title:** Call external programs for decompression.

## Description

Python's built-in compression modules (`gzip`, `bz2` and `lzma`) are slow, whereas calling external programs is much faster. This simple change improves performance by 100%+.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8ce100487b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.