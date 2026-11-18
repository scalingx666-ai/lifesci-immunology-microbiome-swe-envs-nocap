# Issue

**Title:** Add some tests for main() behavior

## Description

in particular, test code added in #108.

this PR adds test infrastructure for testing argument passing in main(), and file creation etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bc0d20bf524`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.