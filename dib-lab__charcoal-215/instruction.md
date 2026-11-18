# Issue

**Title:** [MRG] update default db to rs207 reps

## Description

Addresses #212 by updating to the GTDB rs207 reps database by default. Notes of potential importance:
1. downloads the full gtdb rs207 lineage file, not reps. Other than taking up space, this doesn't change how charcoal runs.
2. changes scaled value from 1000 -> 2000, which is the scaled value reps is built at. May cause some short contigs to be missed that previously were detectable, but I think the benefit is outweighed having the larger database.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75e0324f697e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.