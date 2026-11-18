# Issue

**Title:** Added Model Comparison and Graphics tooling

## Description

This PR introduces tools for model comparison including:
* visualization tools for
  *  ACSetTransformations of PetriNets
  * Multispans of PetriNets
  * Subobjects of PetriNets.
* functions for calculating homomorphisms between PetriNets

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2d9958bef05`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.