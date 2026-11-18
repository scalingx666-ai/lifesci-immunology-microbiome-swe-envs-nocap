# Issue

**Title:** /api/v1/study/1/samples accepts new categories

## Description

calling PATCH on /api/v1/study/1/samples now silently accepts metadata with new categories in them when updating a sample or adding a new one. Existing samples will be assigned a null value while samples in the metadata will be assigned the value or empty string if one was not given.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ceadff125bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.