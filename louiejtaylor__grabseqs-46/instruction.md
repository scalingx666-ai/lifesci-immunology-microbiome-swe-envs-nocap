# Issue

**Title:** Abstract sample and project parsing logic from __init__.py

## Description

This PR moves the logic for looping through sample/project accessions to their corresponding submodules--this is a design decision that I think makes it easier to understand the code, since now all the download logic is in the same place/module.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13ec858f0069`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.