# Issue

**Title:** fix rename missing output

## Description

- map.tsv and original.fasta were saved to workdir instead of output_dir

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9b156143e23`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.