# Issue

**Title:** [MRG] Add checkpoints to hashval query to enable read extraction with one run

## Description

This PR addresses #242 point 1. It uses snakemake checkpoints to solve for the output files of rule `hashval_query`, which then produces each output for rule `extract_reads_single_hashval_file`.

Still needs to be tested :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c590e2a388b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.