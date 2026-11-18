# Issue

**Title:** Fix hardcoded symbols in bilayer net compilation

## Description

This PR ensures that all symbols passed as arguments to the `compile` function are respected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ec06dd7bdad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.