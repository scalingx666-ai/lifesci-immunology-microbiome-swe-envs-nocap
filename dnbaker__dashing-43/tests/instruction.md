# Issue

**Title:** Parallel build fix

## Description

`mv libzstd.a ..` was causing a race condition in submodule bonsai during multithreaded compilation. Fixes the other half of

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e03ff248da73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.