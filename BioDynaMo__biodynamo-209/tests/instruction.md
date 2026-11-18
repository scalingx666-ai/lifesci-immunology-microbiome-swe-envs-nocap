# Issue

**Title:** TF1 thread safety

## Description

As discussed with @LukasBreitwieser :

Added tests that expose the segfault behavior of initializing multiple `UserDefinendRng_D` in parallel.

Call `ROOT::EnableThreadSafety()` to fix this problem.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ee51cdb5f77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.