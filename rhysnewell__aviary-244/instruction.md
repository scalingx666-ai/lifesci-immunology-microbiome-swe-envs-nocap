# Issue

**Title:** Add TaxVAMB

## Description

- [x] Run integration test
- [x] Run real-world test

Adds new env variable (METABULI_DB_PATH) for location of metabuli database. Added to downloads too.
Metabuli produces the best taxonomic labels according to the [TaxVAMB paper](https://www.biorxiv.org/content/10.1101/2024.10.25.620172v1.full).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7cf255ad97d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.