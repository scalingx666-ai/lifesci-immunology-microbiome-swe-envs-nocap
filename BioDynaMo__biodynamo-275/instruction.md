# Issue

**Title:** Fix notebook packages on CentOS

## Description

Fixes python dependencies for CentOS and BDM notebooks. Thanks @Senui for pointing that out!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8376a41b861b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.