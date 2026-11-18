# Issue

**Title:** plot_taxa_prev fix

## Description

`phyloseq::otu_table()` changed to `microbiome::abundances()` to deal with situations where `taxa_are_rows==FALSE`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3e83a5fd9cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.