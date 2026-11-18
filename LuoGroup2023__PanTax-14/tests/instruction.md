# Issue

**Title:** The genomeID in the genomes_info file is considered the genome identifier

## Description

Changelog
---
+ The `genomeID` in the genomes_information file is considered a genome identifier, no longer just manually split based on `RefSeq` or `GTDB`. 
+ `GenomeID` cannot contain special characters of type `#`. 
+ Only implemented in the main `PanTax` program, not in `data_preprocessing`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b50bd7db69f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.