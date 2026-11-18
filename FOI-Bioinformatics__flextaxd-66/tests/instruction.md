# Issue

**Title:** Krakenuniq databases can now be made from a FTD-database + minor fixes

## Description

-Added error handling for when missing genomes cannot be found within NCBI download
-Changed behaviour for warning of missing samples, it is now displayed when datasets are missing from the flextaxd-DB and the user did not specify download from GTDB.
-Fixed so krakenuniq databases can be created (previouly resulted in errors)
  - Argument "--skip_maps" is no longer attempted onto krakenuniq (it is not an argument possible in krakenuniq)
  - taxid2seqid is now placed according to krakenuniq specification
  - taxid2seqid no longer contain empty rows
- logger CMDs are written properly depending on krakenuniq/kraken2/"other" software

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99259f53c2c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.