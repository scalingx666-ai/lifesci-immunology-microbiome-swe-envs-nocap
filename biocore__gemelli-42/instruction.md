# Issue

**Title:** Loads tree in NewickFormat, uses BP to parse tree faster

## Description

Uses BP to parse tree to improve Phylo-RPCA's memory usage. I also updated the setup.py to account for new dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a4cb59f31f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.