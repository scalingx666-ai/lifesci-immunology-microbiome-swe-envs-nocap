# Issue

**Title:** Bugfix/multi db kmer window params

## Description

fix #189 

--window-size and --kmer-size are now passed by hierarchy level, not by database from the wrapper to cpp.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34da226cb80e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.