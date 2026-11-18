# Issue

**Title:** bug fix for phylo RPCA

## Description

When using QIIME2 phylogenic RPCA, the taxonomy was being based as a QIIME2 Metadata instead of a pandas data frame (fixes issue #57). This adds a fix that is already in CTF but was missing in RPCA after the last version merge. 

This will move Gemelli to version 0.0.8, to cover this bug that would break use in QIIME2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c1647bc53e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.