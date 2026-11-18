# Issue

**Title:** Bugfix: Do not RELU latent in clustering

## Description

Commit fc31a8a accidentally set `matrix[matrix < 0] = 0`, hence destroying 50% of information in the latent space. This led to a serious quality regression in Vamb, as discovered by Xinyuan.

Also check that the new PCG64-based shuffling works correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f491b603c64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.