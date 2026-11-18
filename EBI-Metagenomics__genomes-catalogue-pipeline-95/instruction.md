# Issue

**Title:** Checkm2

## Description

Changed the QC tool from CheckM to CheckM2. Enabled NCBI genomes to be processed - NCBI genomes are taken through CheckM2, ENA genomes are expected to have completeness and contamination data provided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2937a0ba4b85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.