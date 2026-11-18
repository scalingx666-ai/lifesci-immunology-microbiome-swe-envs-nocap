# Issue

**Title:** NumPy-based motif generation

## Description

Improves performance of the `ClusteringResult.summary()` method (~20x faster), with identical results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5bf5ee577d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.