# Issue

**Title:** Add support for dimred to getCrossAssociation

## Description

This PR adds support for dimred to getCrossAssociation function. The option is fully working, but is currently hidden to avoid excessive number of parameters, and to allow us to test it first. This could be used to calculate correlation between features and PCoA coordinates.

This is related to this issue:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6192112b9294`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.