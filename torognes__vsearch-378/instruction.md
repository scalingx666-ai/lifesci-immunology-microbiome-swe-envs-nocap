# Issue

**Title:** FIX: silence fastq_stats() if --quiet

## Description

Just a small fix to really silence `fastq_stats()` if `--quiet` is set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13e37faec86c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.