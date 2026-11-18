# Issue

**Title:** Replace NULL with nullptr in C++ sources

## Description

## Summary
Replaced 3 uses of the C macro `NULL` with C++ `nullptr` in `command_line_options.cc`, `mapped_data_array.h`, and `benchmark/main.cc`.

## Test plan
- [ ] Verify project builds successfully on CI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f87d383c73b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.