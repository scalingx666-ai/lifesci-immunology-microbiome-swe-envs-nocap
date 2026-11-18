# Issue

**Title:** added suffix collapse

## Description

This PR adds a new function to the `collapse` command: it now can treat feature IDs like "G000123456_789" as genome-gene stratified features, and collapse on either the genomes or the genes. With this function, one no longer needs to do genome-gene (i.e., OGU-ORF) stratification from `classify`. Instead, one can just generate a gene (ORF) profile, and collapse it to both higher taxonomic and functional levels as a stratified profile.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `774fbb8762b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.