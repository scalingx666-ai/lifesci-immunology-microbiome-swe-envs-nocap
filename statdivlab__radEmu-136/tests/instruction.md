# Issue

**Title:** Fix zero comparison

## Description

Address issue #135 to avoid mistakenly flagging parameters as "zero-comparison" when we have a design matrix that involves an ordered factor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae7f845faaac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.