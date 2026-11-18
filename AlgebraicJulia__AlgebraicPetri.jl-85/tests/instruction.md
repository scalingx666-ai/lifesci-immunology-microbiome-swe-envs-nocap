# Issue

**Title:** Constructors of Petri net types are too loose

## Description

Because they accept essentially any arguments, they create method ambiguities with standard acset constructors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee3d2c92edd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.