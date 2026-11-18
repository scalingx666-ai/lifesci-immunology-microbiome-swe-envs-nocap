# Issue

**Title:** Reduce use of ValueError

## Description

Some uses of ValueError were inappropriate. This generalizes most of
them to be an Exception.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa9cef33b08d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.