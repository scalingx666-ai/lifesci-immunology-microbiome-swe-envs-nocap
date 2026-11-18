# Issue

**Title:** Calculate sequence variation in cluster

## Description

calc_variation() metric added that calculates average variation per AA position. Variation is here defined as the information content as defined by the Shannon entropy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b065016a07c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.