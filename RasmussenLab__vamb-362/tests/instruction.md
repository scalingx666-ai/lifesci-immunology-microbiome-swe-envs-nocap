# Issue

**Title:** Fix cuda utilization and CLI for Taxometer

## Description

Two changes:
- fixed a bug where not all the Taxometer layers are transfered to GPU
- removed the batch steps for all the taxonomy models (Taxometer and TaxVAMB) with corresponding test changes.

Solves  and

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdd14d128550`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.