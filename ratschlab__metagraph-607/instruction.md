# Issue

**Title:** MADV_RANDOM for graphs loaded with mmap

## Description

PR Review: Optional `MADV_RANDOM` for mmap-loaded graphs

Summary

This branch adds a new `--madv-random` CLI flag that, when used with `--mmap`, calls `madvise(MADV_RANDOM)` on the graph's memory-mapped region after loading. The intent is to disable kernel read-ahead, which benefits small random-access queries but may hurt sequential scans.

For annotations (queried in ordered batches), `madvise` only made it slower, so we don't do `madvise` for that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e69e1282f551`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.