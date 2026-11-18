# Issue

**Title:** use unique temp prefix in samtools sort

## Description

The fixed `/tmp/aln.sorted` prefix will cause error on
multiple jobs running in the same node.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36bdaa75459c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.