# Issue

**Title:** Clear invalidated medoid cache on packing

## Description

Packing the indices of a ClusterGenerator shifts the meaning of the integers in its cache, invalidating it.
I suppose they could be updated in the cache, but that'd be a complex piece of code a clustering implementation which is already too complex for its own good. Instead, clear the cache when packing.

This should happen a neglible amount of times compared to how often we already clear the cache.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21bdcdd7f607`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.