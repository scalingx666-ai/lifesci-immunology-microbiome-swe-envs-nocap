# Issue

**Title:** Remove serial mode

## Description

Remove serial mode, leave current test infrastructure intact but search tests with SIMD only

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf67dbbbea15`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.