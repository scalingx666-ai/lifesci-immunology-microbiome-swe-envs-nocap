# Issue

**Title:** Contig export with genes of interest

## Description

This PR introduces a new flag to `anvi-export-contigs` so it can export sequences of contigs (or splits) from a `contigs-db` file that encode one or more of the gene calls the user declares with the new flag `--gene-calls-of-interest`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4646ee059ea5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.