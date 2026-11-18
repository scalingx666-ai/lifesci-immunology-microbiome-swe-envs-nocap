# Issue

**Title:** Patches to allow MMseqs2 to build with gcc13

## Description

Due to changes in the way it handles includes, `MMseqs2` wasn't building with `gcc13`. These 4 files required patching to make them behave ...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71dd32ec43e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.