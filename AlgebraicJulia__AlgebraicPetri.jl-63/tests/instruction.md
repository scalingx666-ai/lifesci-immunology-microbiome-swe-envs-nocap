# Issue

**Title:** Update Catalyst Interop

## Description

The transition from Catalyst v6.13 to v6.14 introduces changes which currently break the AlgebraicPetri interop tools. This PR adds a compatibility requirement until the interop tools have been updated to support Catalyst v6.14

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bb2b6020fb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.