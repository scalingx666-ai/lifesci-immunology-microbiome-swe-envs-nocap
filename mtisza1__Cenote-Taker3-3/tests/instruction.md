# Issue

**Title:** Update2: to v3.2.1

## Description

Changes:

1) Added `-wd`/`--working_directory` flags for specifying working directory for outputs
2) Added pyarrow to enviroment files. Prevents pandas futurewarning.
3) Fixed downcasting in `fillna()` commands in python/pandas
4) Fixed paths so that hhsuite databases are download and referred to correctly
5) Added `--genbank` flag which allows users to disable genbank outputs
6) Fixed taxonomy lineage parsing in `vote_taxonomy.py` in certain cases.
7) Fixed `hhpred_to_table.py` parsing of hhsuite output files to correctly hand CDD and PDB accessions/descriptions.
9) Updated scripts so that in annotation mode `-am True` (unless flag `--caller adaptive`) to skip unnecessary initial `pyhmmer` steps. This reduced runtime by about 25%.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b48a741eb58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.