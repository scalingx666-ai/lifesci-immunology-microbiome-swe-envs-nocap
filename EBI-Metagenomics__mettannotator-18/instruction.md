# Issue

**Title:** Fix update gff with mapped uniprot ids

## Description

Refactored script, added fixes for when the Dbxref field already exists.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60dda84e6e12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.