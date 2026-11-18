# Issue

**Title:** BUG Fix for very short peptides

## Description

Pad with sequence with 'X'. The result is kind of fake and we warn the user, but we no longer crash.

close #40

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4267c99830e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.