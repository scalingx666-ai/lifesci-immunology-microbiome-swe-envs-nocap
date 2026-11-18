# Issue

**Title:** Make long read qc temp

## Description

The cost to storage is not worth having an extra copy of your nanopore reads sitting around just to save time during the QC stage. If users are unaware that they can delete this file then we'll quickly be filling up peoples servers with junk.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19b803b7c159`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.