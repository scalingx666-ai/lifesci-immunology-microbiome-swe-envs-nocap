# Issue

**Title:** Use torch's nonzero in smaller_indices

## Description

We used to convert to Numpy, call nonzero, then convert back to Torch, since the Numpy implementation was faster.
It no longer is, so I remove this needless optimization

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72f388d27aee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.