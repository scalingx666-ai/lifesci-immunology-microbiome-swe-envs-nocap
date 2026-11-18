# Issue

**Title:** Edits to allow trackB = TRUE in fit_null to actually do anything / work.

## Description

Code updates to allow trackB= TRUE in fit_null.R to do anything / actually return a data.frame of parameter values throughout optimization. Also add test that trackB is runnable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8a9af28dd59`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.