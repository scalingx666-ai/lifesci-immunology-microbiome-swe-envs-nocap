# Issue

**Title:** [Fix] correct CIGAR string in SAM format as well as correct header in…

## Description

… bam format

Already known problem with macth/record qLength entries.
Wrong number of sequences used for the BAM header

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfc0b5b205bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.