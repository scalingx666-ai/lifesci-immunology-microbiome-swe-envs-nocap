# Issue

**Title:** Refine zeromask check in latent normalization

## Description

Previously, to check if every feature of a contig's latent representation was zero, Vamb checked if the mean was zero. This caused a small risk that a contig with nonzero latent space would happen to sum to zero. Now, instead check if the largest value is zero.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b486b6fa7e6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.