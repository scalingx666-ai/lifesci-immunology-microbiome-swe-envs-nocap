# Issue

**Title:** attempt to fix issues with megahit inputs

## Description

This is an attempt to fix contig mismatching reported in #3 that happens with MegaHIT inputs.

Fix relates to , and my comment later in that issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d870b0f97819`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.