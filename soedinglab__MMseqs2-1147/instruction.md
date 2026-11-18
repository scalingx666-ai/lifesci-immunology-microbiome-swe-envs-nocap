# Issue

**Title:** Fail instead of writing wrong --createdb-mode 3 cluster results

## Description

Barrier files start with the SLURM job, step and restart count, so a file that a killed run left is waited past instead of read; before, a stale exchange index let createtsv exit 0 with most lines missing.

A database read on a different number of nodes than it has files, a torn cluster index, more keys than the build holds, a key in two clusters or past the database, a cluster without its rep line and received members that are no entry in key order now fail.

createtsv rejects options it ignored on mode 3 and clusterings of another kind, mergeclusters more than two clusterings, and both take --split-memory-limit as the original createtsv-linfinity did.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `474b987df5f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.