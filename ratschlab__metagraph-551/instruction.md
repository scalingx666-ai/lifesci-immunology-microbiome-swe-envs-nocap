# Issue

**Title:** Optimization of single-threaded RowDiff queries

## Description

Added `RowDiff::get_rows_dict` that doesn't split rows into blocks for single-threaded queries.

This speeds up single-threaded queries with `--mmap` by >30%

Also:
* execute every request in server with a single thread
* logging improvements in server

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a78b5374217`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.