# Issue

**Title:** Enforce `max_clusters` is not set with VAEAAE model

## Description

In `__main__.py`, the AAE Y and AAE Z clusters are both written to a clusters file. However, if I understand correctly, training the AAE latent directly gives you the full clustering of the AAE Y latent space. In contrast, the AAE Z latent space requires running the clustering algorithm.
However, if a user sets `-c` (i.e. limits the number of output clusters), then Y and Z will differ in that Y contains the full set of clusters and Z only a subset.

The solution in this PR is to simply disallow the `-c` option together with the `vae-aae` model.

CC @Paupiera - can you review (and approve and/or comment on) this bugfix?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a235e497f482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.