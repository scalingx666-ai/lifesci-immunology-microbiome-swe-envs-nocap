# Issue

**Title:** fix typos hindering expandable profile db to be merged properly

## Description

fixing minor typos where `tsv2exprofieldb` not passing `MMSEQS_FORCE_MERGE=1` flag properly when calling `mmseqs compress` module

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4841a8efad0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.