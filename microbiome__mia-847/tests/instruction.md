# Issue

**Title:** Add Allen's phylogenetic entropy and Rao's quadratic entropy to addAlpha

## Description

. Adds abundance-weighted phylogenetic alpha diversity indices—Allen's phylogenetic entropy (`allen`) and Rao's quadratic entropy (`rao`)—to `getAlpha()` and `addAlpha()` via single-pass postorder tree traversal in `.calc_tree_diversity()`, unifying tree extraction with Faith's index and adding unit tests for aliases, missing trees, and star-tree equivalence to Shannon and Gini-Simpson.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4884e76c3ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.