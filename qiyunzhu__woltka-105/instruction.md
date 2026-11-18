# Issue

**Title:** handled zero length alignment

## Description

In some situations, an alignment record may appear to be intact, but the length of the alignment is zero or not available. This happens when one runs Bowtie2 with default parameters on a paired-end sequencing dataset, which could result in some lines whose CIGAR is "*" (not available). This patch lets the program skip lines without alignment length, rather than raise an error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2356db53ac7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.