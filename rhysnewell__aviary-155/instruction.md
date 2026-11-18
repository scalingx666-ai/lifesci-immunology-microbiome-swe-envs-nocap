# Issue

**Title:** Fix short read coassemble qc

## Description

Output path should be passed to cat_reads, not file handle.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9de55977c3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.