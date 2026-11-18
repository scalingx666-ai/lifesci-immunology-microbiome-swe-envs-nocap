# Issue

**Title:** Align cluster names from Z, Y and VAE space.

## Description

Previously, VAE and Y clusters were named "vae_\d+" and "aae_y_\d+", whereas Z clusters were named "aae_z\d+" (with a missing underscore). Add the missing underscore to the cluster names.

Closes issue #150

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b07a952fdda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.