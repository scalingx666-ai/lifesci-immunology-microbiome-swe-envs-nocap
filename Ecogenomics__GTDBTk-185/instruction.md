# Issue

**Title:** Display progress updates

## Description

hmmalign and fastANI progress shown in console.
Changed how jobs in multiprocessing queue for the aforementioned tasks are handled. Instead of partitioning, it's consumed from a shared queue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fd8c242e1a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.