# Issue

**Title:** updating remove hostreads paired

## Description

- Add a 2step approach for dsync'd fastq paired-end reads. First, assumes sorted R1/R2 and pulls out with standard samtools flag. If that fails, skip to iterating through each line by line as a failsafe (which is much slower) to address irregular formats for input file(s).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1ec6a6b12fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.