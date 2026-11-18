# Issue

**Title:** Fix envs

## Description

Changes to environments.
- Add fuzzy matching to problematic environments (dastool, semibin)
- Added full channel set to environments (some only had bioconda)

Bug fix for edge case in `Filter-Complete-Contigs.py`: Dataset consisting of only bins with 100% completeness raises an error in plotting the histogram due to improper bin sizes. Bug fix adds conditional statement to handle this case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ae6ca8e02c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.