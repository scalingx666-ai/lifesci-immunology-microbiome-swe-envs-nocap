# Issue

**Title:** EXP: Revert "Build(deps): Bump pypa/cibuildwheel from 2.23.3 to 3.0.0

## Description

#3687 seems to have broken the ubuntu x86_64 wheel builds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc74a5b4a989`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.