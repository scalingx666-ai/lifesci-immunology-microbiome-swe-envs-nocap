# Issue

**Title:** trim fasta header to 20 chars fixes #149

## Description

Fix to trim any input fasta headers to ensure that they are 20 chars or smaller, so as not to break hh-suite

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a1e04c87f89`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.