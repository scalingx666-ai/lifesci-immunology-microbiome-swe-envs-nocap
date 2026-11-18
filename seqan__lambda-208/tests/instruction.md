# Issue

**Title:** feat: allow multithreaded fmindex construction

## Description

- updates to newest fmindex
- uses fmindex_collection now uses libsais instead of libdivsufsort
- support for openmp
- adds option to control the thread count for suffix array construction

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `312d4eb846ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.