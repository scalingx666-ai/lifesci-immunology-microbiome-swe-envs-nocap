# Issue

**Title:** Add clang-format code-style check to GHA

## Description

Add GHA that quickly checks the code style with clang-format.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1deac71154bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.