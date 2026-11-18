# Issue

**Title:** add general purpose function to depart nodes from the dat object

## Description

.

I called it `depart_nodes` instead of `delete_nodes` because in the `networkDynamic` case you deactivate the nodes rather than actually deleting them from the `networkDynamic` (which is a different operation).  We also have a `delete_vertices` function for edgelists, and I can imagine `delete_vertices` and `delete_nodes` getting confused with each other.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6bb2d772c2a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.