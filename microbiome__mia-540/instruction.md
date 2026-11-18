# Issue

**Title:** Temporal fix for rworkflow bug

## Description

This commit provides a temporal fix to rworkflow by bumping the r version of MacOS and Ubuntu and
fixing a  bug in R/estimateDiversity.R.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a0b0ead9d82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.