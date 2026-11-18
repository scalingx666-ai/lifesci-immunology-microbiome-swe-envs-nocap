# Issue

**Title:** Merge dev into master

## Description

* swaps GOB to MessagePack for storing index
* exposes maxK and numPartitions for LSH Ensemble
* replaces existing hash functions for MinHash with ntHash
* adds some more unit tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f68050acd91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.