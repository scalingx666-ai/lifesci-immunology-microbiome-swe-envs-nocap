# Issue

**Title:** Test basic workflows

## Description

- [ ] Does this PR change the contracted DBG, catlas, or minhash DB formats?
      If so, merge with care as this will require rebuilding some big files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0b9dbd5841a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.