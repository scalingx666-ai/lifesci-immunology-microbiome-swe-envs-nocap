# Issue

**Title:** Add benchmarking to prepare_binning_files rules

## Description

Added benchmarks to the 3 rules in prepare_binning_files:
 - prepare_binning_files
 - prepare_binning_files_split
 - prepare_binning_files_gather

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04b71a63993c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.