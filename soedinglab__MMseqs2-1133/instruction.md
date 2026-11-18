# Issue

**Title:** Fix 32-bit legacy mapping file compatibility problem

## Description

It had a breaking change in magic number along with 64-bit patch, without any legacy file compatible codes.
Here, I added a small bit of code enabling it to properly parse legacy binary mapping file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c77b5afa910b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.