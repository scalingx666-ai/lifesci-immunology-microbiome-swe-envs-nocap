# Issue

**Title:** fixed so genomes missing in flextaxd-database are downloaded from...

## Description

GTDB. The fix includes:

- If directory for genome sequences does not exist, notify the user and prompt for creation of directory
- Syntax error and mis-spelled variable
- Download of the proper file from GTDB (previous: bac120_marker_genes_reps.tar.gz, now: gtdb_genomes_reps.tar.gz)
  - I believe the code is not designed to parse the structure for marker_genes.
  - Note: The download of GTDB rep-set is slow.
  - Suggestion: Download missing accessions using NCBI "datasets" tool

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e7c812d1d131`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.