# Issue

**Title:** Bug fix/organising script

## Description

Bug/format fixes:

- added "genomes1" as part of the path to genomes
- modified RNAcentral script to account for changes in ENA and ENA format inconsistencies

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `155e230fcef8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.