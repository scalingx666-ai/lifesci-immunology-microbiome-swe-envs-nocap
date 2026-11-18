# Issue

**Title:** Fixed path to modules

## Description

We moved get_ENA_metadata.py and utils.py to the bin folder which broke fetch_ena.py and fetch_ncbi.py. Added relative paths to both scripts to fetch the modules.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5604d50399a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.