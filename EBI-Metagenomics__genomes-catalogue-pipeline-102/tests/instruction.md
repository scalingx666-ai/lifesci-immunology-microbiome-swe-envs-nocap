# Issue

**Title:** Update fetching script

## Description

Added a flag to skip QS50 filtering. If used, the script will fetch all genomes from ENA regardless of whether they pass the QS50 threshold.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c61dda230cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.