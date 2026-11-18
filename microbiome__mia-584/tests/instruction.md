# Issue

**Title:** Deprecate z transform in transformAssay

## Description

This commit does the following:
1-  Deprecates the z method in transformAssay
2- Updates the documentation to  only reference transformation methods already present in vegan::decostand.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `803500301568`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.