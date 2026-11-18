# Issue

**Title:** Removed splitting scaffolds into contigs

## Description

Stats calculation fix - the original script split contigs into multiple ones if "N" was present. Removed this feature.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c92cd63aa6c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.