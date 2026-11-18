# Issue

**Title:** fix get_sims

## Description

correctly saves `_last_unique_id` and `el.cuml` when extracting simulations with `get_sims`. 
This fixes the duplicated unique IDs when restarting simulations where the restart point was part of a batch

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18b6c58abed2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.