# Issue

**Title:** Add flag to turn off gradient computation for DG

## Description

If we have multiple DG but only need the gradient information for one of them, we're doing a lot of unnecessary computation. This PR adds a flag to turn off the gradient computation such that this can be avoided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7242e5b9e524`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.