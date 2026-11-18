# Issue

**Title:** 216 minimap2 failing due to io error on aws ec2 batch jobs

## Description

- Fixing minimap2 to use a 2step process
1. Align
2. Samtools sort

- Add failsafe split prefix

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fd1fb5bb236`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.