# Issue

**Title:** nproc without all flag returns 1 inside snakemake

## Description

When executing the script from snakemake, the output of nproc return 1, ending the script. Added --all flag to ensure all avalible threads are detected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e90d86649769`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.