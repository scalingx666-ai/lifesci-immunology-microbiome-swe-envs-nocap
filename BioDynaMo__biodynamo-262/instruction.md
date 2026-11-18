# Issue

**Title:** Fix possible race condition in user-defined thread-safety mechanism

## Description

In the critical region, disallow duplicates and null pointers.
This can happen, because a call to Agent::CriticalRegion is not protected.
Therefore, another thread can change it before the locks are acquired.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f8acc15bafd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.