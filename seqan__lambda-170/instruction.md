# Issue

**Title:** Fix bs untrue query and subject id and add bs tests

## Description

I added the bs tests separately so far because they don't go through SIMD mode currently. Later we can add them as separate program and only have one loop for all.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1dad22d29ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.