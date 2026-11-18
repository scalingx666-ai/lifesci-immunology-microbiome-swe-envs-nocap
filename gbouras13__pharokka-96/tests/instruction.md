# Issue

**Title:** trna pseudogene fixes #90

## Description

Fixes bug where phrokka breaks when trnascan-SE identified pseudogenes. This commit adds pseudogenes into the .gff and .tbl files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a4eeef7b250`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.