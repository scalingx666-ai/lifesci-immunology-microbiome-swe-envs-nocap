# Issue

**Title:** Added auto-mem, input file validation and may have fixed gpu-mem option.

## Description

I have a version of megahit that implements an auto memory setting option.  This version also allows verification of input files and sets gpu-mem.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f4c93b865bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.