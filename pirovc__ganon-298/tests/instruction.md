# Issue

**Title:** ganon v2.1.1

## Description

- Change terminology from representatives to reference genomes  https://ncbiinsights.ncbi.nlm.nih.gov/2024/09/25/updated-terminology-reference-genome/
- Fix genome size estimation for GTDB databases
- Updated docs
- Added `--normalize` argument on `ganon report`
- Remove checks on raptor calls

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68f51b79065b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.