# Issue

**Title:** Fix 258

## Description

This PR converts treeData from a dictionary to an array. One thing to note is that the first element of treeData is 0. This is equivalent to null and exists because currently empress uses 1-based index for postorder positions. This will be removed in #223.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b551bd7db4ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.