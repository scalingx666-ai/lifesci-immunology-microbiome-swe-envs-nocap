# Issue

**Title:** Deterministic gene caller IDs

## Description

Finally a fix for the issue raised here: #2551 
A simple switch from imap_unordered() to imap() and now gene caller IDs will be deterministic and not change between to run of anvi-gen-contigs-database with different threads count.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6899acbd8170`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.