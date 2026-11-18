# Issue

**Title:** Minor build improvements

## Description

BWA and Samtools are now stripped for a smaller final blob.

The Dockerfile now builds a static binary that includes bwa/samtools.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d9a62038cf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.