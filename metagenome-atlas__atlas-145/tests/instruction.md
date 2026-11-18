# Issue

**Title:** Dev

## Description

Bug fixes in:
Binning workflow: 
- Renaming of genomes

Gene catalog:
- get gene_catalog.faa with amino acids
- predict single copy genes
- added gene catalog to the output of 'atlas assemble'
- temporarily removed gene annotation form output of 'atlas assemble'

I will work on a different branch to make annotation of the gene catalog instead of each gene in each sample. 

FYI @brwnj @sofie8

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab60086fef60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.