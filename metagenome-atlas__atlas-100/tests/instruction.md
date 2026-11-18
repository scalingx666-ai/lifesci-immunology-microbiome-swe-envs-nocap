# Issue

**Title:** corrected memory allocation for samtools

## Description

as there are two chained samtools execution they exceed memory limits.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54ca329617d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.