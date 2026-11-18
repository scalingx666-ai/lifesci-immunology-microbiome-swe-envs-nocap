# Issue

**Title:** DSL2: Add nf-test microbial

## Description

Linked to #1138 

nf-test conversion for `test_microbial`

Still need to check that all files are picked up by snapshots, this is just the initial setup, using the `test` profile as a guide.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50b039f60e4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.