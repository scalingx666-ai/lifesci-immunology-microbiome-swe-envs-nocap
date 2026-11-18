# Issue

**Title:** Fixed building of Newick-tree in visualization that previously lacked…

## Description

… some nodes. Added sanity-check that compares number of nodes in database compared to Newick-tree.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6cf4ab06493`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.