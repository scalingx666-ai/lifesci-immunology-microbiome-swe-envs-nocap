# Issue

**Title:** Use minimum mapping quality in pileup

## Description

This PR adds the parameter `minmapq` to the `pileup.sh` script. The atlas config parameter used is named `minimum_map_quality` and was added to the default config with the value of `0`. This means that from the user perspective nothing has changed in the default behaviour of atlas, however the map quality can now easily be adjusted via the config file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `359867c48e4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.