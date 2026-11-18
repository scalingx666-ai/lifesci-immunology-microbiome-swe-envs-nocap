# Issue

**Title:** tests: replace manual file reads with fs::read_to_string

## Description

Since all the tests read the temporary files as string values, we are better off using the `fs::read_to_string` function for assertions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df0ba3870036`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.