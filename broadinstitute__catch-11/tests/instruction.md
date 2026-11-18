# Issue

**Title:** Add tools to pool probes across datasets

## Description

When pooling probes across multiple datasets, we would like to find optimal parameters for each dataset subject to a constraint on the total number of probes in the pool.

This is heavily based on the script `find_optimal_params.py` in @haydenm's `hybsel-design-runs` repo.

Modules containing functions to search the space of parameters are in `hybseldesign/pool/`. The script to run these procedures is `bin/pool_probes.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33a3b9d71cb7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.