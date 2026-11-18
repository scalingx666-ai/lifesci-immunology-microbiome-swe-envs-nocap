# Issue

**Title:** Feature/update ubuntu to xenial

## Description

Ubuntu environment on Travis updated to 16.04 Xenial:

- clang 7 and 8
- gcc 8 and 9 (yeahow!)

We could probably already updated to 18.04 as well, but one step at a time...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4dd6a5a6ded`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.