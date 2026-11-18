# Issue

**Title:** Download files

## Description

The download function was reimplemented and will use ncbi-genome-download in the background to retrieve as many genomes as possible annotated in the database.

There may still be a bug in that one thread was getting stuck during testing, please report the issue if it seems reproducible!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e11c076300a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.