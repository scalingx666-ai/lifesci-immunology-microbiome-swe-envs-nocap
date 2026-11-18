# Issue

**Title:** Rnacentral updates

## Description

- Brought the RNAcentral script up to date with the pipeline changes (including the switch to tRNAscan-SE)
- Added accounting for private samples
- Added accounting for previous catalogue versions
- Added unit tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93e42ec7a1b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.