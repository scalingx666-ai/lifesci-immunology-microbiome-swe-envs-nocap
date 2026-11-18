# Issue

**Title:** Warn users on too few contigs

## Description

Now warn users already when parsing contigs if they have fewer than 20,000 sequences, in order to prevent users from accidentally overfit the VAE.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb1e11743df6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.