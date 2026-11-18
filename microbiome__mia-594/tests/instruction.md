# Issue

**Title:** Remove tree rooting in calculateUnifrac

## Description

This PR changes `calculateUnifrac` so it doesn't **change tree**(_root tree_) before calculating unifrac distance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e62a04e8fb2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.