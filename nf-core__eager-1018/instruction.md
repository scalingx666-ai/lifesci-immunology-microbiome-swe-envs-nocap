# Issue

**Title:** DSL2: Pull input files from reference sheet columns

## Description

This PR edits the input of files to be through the reference indexing subworkflow both for single and multiple references.

Adds input for these files:
- HapMap file for angsd contamination estimation
- SNP bed file and masked fasta for pmdtools
- SNP bed for genotyping
- SNP eigenstrat file for pileupcaller
- SNP bed for sexdeterrmine
- SNP bed for qualimap
- Analysis file for bedtools

This .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc9c7b5ff766`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.