# Issue

**Title:** Fixing proteom for ensembl genomes species, issue 84

## Description

Generalized getProteome to the new format for ensembl. 

Fix for 

EnsemblGenomes species now work for proteome, added also a new test to verify it works.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbbfb566923e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.