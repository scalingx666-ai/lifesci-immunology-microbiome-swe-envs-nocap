# Issue

**Title:** Truncate the GFF end boundry for circular prophages

## Description

This is because VirSorter2 introduces an artifact for circular genomes. See - 

We have decided to truncate that so the GFF is valid. I've added a bit in the documentation about them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a099ef914f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.