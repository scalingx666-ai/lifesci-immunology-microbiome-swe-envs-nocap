# Issue

**Title:** Prevent generate_extra_weight_table.py from bailing out if a genome is missing.

## Description

Missing genomes at this step may have been removed in the QC step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f5bd980da66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.