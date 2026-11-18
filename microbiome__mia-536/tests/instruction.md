# Issue

**Title:** Rename subsampleCounts to rarefyAssay

## Description

This PR makes the following naming modifications : 

- `subsampleCounts` --> `rarefyAssay`

The man page subsampleCounts becomes rarefyAssay to avoid duplicated aliases with the deprecate man page.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d264b8c374a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.