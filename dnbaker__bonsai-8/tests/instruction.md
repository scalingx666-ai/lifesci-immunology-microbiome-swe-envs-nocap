# Issue

**Title:** Replace std::list with FastCircularQueue

## Description

This eliminates news/deletes from the QueueMap data structure and improves locality. This might not make much of a difference, but reducing memory management contention and cache coherence should at least not be a bad thing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7ed3a916aed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.