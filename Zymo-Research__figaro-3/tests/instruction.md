# Issue

**Title:** Fixed issue with Zymo naming standard

## Description

Fixed issue where zymo naming standard files fail during the initial estimation of data size.  Naming standard preferences were not being passed successfully to this function.  This has been fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2347fcc0ce53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.