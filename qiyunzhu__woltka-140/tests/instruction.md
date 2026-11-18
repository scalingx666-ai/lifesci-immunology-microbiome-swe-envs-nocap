# Issue

**Title:** [WIP] Optimization of ordinal mapping using Numba

## Description

This has so far achieved some 35% reduction in memory usage and 33% reduction in runtime. However, multiple issues were encountered with during coding with Numba. I envision that deployment with Numba won't be easy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cc9516afeb6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.