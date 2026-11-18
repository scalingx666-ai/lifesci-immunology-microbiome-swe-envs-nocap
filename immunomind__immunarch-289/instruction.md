# Issue

**Title:** seqCluster fix of multiple cluster assignment

## Description

Fix bug while same sequencies belongs to different V and J genes multiplies in result of clustering;

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca2541d1d83f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.