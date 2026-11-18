# Issue

**Title:** Added MDMcleaner and nanopore support for bin_reassembly module

## Description

- Added boolean flag `--mdmcleaner`, which then make the reassembly module parse the output of bin filtering after MDMcleaner. See MDMcleaner [here](https://github.com/KIT-IBG-5/mdmcleaner)
- Added `--nanopore` flag. Reads are aligned with minimap2, splited into bins and then are supplied with `--nanopore` flag to spades for both: strict and permissive assemblies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f5411987016`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.