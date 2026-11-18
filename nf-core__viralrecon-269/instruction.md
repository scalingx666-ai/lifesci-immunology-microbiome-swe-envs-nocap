# Issue

**Title:** Add long format table to ONT output

## Description

Complementary to  

## TODO

- [x] Update BCFTools Query args in `modules_nanopore.config`
- [x] Update long table Python script to parse BCFTools Query file for `--artic_minion_caller nanopolish` and `--artic_minion_caller medaka`
- [x] Double-check format of final output table for `--artic_minion_caller nanopolish` and `--artic_minion_caller medaka` is the same as with Illumina.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ef0550fe621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.