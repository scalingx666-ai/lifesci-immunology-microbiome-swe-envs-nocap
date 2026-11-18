# Issue

**Title:** BUG/PERF: avoid dense conversion of biom

## Description

This change reduces memory required to process the EMP by 140GB, and spin up runtime by 24 minutes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33d9d138668a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.