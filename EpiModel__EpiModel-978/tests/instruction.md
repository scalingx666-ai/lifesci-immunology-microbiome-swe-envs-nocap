# Issue

**Title:** Implement more get/set_network across code base

## Description

This PR updates #977 by using `get/set_network` more instead of  `dat$run$nw`.

I left raw accesses in `inits_net` as it's where they are initialized

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56c1d9e3d417`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.