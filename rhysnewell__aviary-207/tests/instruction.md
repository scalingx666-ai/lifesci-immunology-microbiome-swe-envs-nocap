# Issue

**Title:** Update annotation.smkwith new GTDB DB URL

## Description

This gives a 404 error (as of 2024-06-01):
https://data.gtdb.ecogenomic.org/releases/latest/auxillary_files/gtdbtk_data.tar.gz

This seems to be the same file:
https://data.gtdb.ecogenomic.org/releases/latest/auxillary_files/gtdbtk_package/full_package/gtdbtk_data.tar.gz

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86656d0fc4d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.