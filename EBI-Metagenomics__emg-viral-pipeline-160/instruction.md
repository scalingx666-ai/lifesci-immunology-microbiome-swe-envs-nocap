# Issue

**Title:** Add check for many-Ns

## Description

If CheckV tool doesn't find proteins it fails on hmmsearch step. I had a case of contig with many NNNN in sequence. I've added removal procedure for that case

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ae0b94cad5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.