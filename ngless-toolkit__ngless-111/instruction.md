# Issue

**Title:** Fix CIGAR size calculation for insertions

## Description

This  but has potential implications in several code paths (calculation of % identity, which sequence is kept, ...) so requesting a review and further scrutiny before merge.

Tests will likely fail due to #110 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b3e45d76755`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.