# Issue

**Title:** Add sourmash taxonomic profiling

## Description

- Adds a folder with a sourmash taxonomic profiling workflow Snakefile following the same format as other workflows. 
- Adds a conda environment that can be used to install snakemake, and corresponding instructions in README.

Limitations:
 - has not been tested on snakemake below v7.18
 - does not yet contain corresponding tutorial.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16977d494e9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.