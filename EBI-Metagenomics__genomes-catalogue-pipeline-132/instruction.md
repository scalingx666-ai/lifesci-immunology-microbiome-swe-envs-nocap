# Issue

**Title:** Remove trailing slashes from path in fetch_ncbi.py

## Description

A trailing '/' was preventing the correct URL to form. With this change the new URLs are 

`https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/002/255/GCA_000002255.2_Mmul_051212/GCA_000002255.2_Mmul_051212_genomic.fna.gz`

instead of

`https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/002/255/GCA_000002255.2_Mmul_051212//_genomic.fna.gz`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6753b029d9e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.