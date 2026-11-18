# Issue

**Title:** Single Sample addition as input and BBNorm

## Description

1. Update to docs
2. Adding fastq_1, fastq_2, trim, type, sample, seq_summary to parameters for a single sample (alternative to --input samplesheet)
3. Switching KHMER to BBNorm for normalization of reads

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `883732d5d8ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.