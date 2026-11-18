# Issue

**Title:** Fix: In TaxVamb, use Taxometer CLI options for Taxometer

## Description

Previously, the VAEVAE's batch size and epochs were used. Also, delete the -pq option, which was never used, even when set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23dfdef95d6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.