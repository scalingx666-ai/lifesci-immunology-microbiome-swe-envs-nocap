# Issue

**Title:** Fix fasta index

## Description

The pyfastx index for contig file when writting the final bins was not properly set up. 

The index is now the same as when contig are read for the first time: `<outdir>/temporary_files/` .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c15d1f5fcb7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.