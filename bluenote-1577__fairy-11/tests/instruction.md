# Issue

**Title:** fix wrong e literal

## Description

The `e` literal used it wrong (there is a 1 missing in the decimal places)

This replaces it with the `exp` function which should be more readable anyway.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0fe4b340ae44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.