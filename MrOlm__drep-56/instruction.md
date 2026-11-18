# Issue

**Title:** force_overwrite in checkm

## Description

I added force_overwrite to checkm. If dRep fails in the middle of checkm, it will fail in the next try because checkm output dir is not empty

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32d19b1bf528`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.