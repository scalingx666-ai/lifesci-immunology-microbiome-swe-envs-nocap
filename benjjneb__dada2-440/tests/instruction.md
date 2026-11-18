# Issue

**Title:** mergeSequenceTables accepts a vector of files/sequence tables

## Description

Addresses #438 

Backwards-compatible so as not to break anyone's code. Vector of files/sequence tables needs to be provided as a named parameter, e.g. `mergeSequenceTables(tables=mySTs)`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a8bb21d55b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.