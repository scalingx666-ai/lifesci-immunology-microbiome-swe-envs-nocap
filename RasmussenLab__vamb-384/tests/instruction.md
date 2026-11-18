# Issue

**Title:** Also add bin prefix to AAE cluster names

## Description

In commit 905115, the bin files were renamed by adding a prefix in order to resolve a file name conflict between the Z and Y space clusters. However, this meant that the bin/cluster names now did not correspond to the file names of the bins.
Instead, in this commit, rename the bins themselves.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3fe7e03bc04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.