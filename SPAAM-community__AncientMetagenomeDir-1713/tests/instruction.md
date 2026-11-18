# Issue

**Title:** Update GitHub actions to use latest amdirt version

## Description

- Update the GitHub actions workflows to use
  + Python v3.12 instead v3.9
  + amdirt v1.7.0 instead of v1.6.5
- Remove channel `defaults` from `update_images.yml`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db579c15529f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.