# Issue

**Title:** Correct par_reduce bug.

## Description

We had an indexing error in par_reduce yielding incorrect quantities.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d31f6df064da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.