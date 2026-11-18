# Issue

**Title:** Fix: taxa naming in merge_taxa2, see issue 223

## Description

function merge_taxa2 was creating NA annotations for the merged taxon on all taxonomic ranks. See

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4202f6bef33d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.