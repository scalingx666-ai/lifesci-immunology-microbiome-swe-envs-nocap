# Issue

**Title:** Fix qiime2 importer

## Description

The importer failed when the order of samples did not match between abundance table and sample metadata even though they were correct otherwise. The function gave error that told that the datasets are incompatible. Now it is fixed; the correct samples are fetched from the sample metadata despite the order, and user gets informative warnings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4b7e97ba78c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.