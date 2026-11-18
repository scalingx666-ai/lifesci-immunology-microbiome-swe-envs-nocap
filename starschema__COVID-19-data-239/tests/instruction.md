# Issue

**Title:** Fixing METADATA SQL generator

## Description

:

* apostrophes are now double-escaped (`' -> ''`)
* table and column names are in double-quotes to ensure that otherwise reserved names for `METADATA` (`TABLE`, `COLUMN`) will be interpreted correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a166f5ebbd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.