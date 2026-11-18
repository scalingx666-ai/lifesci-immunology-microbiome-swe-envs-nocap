# Issue

**Title:** Fix pigz attempting to zip files that don't exist

## Description

. Calls to pigz/gzip are only made when we know that the file to be zipped actually exists.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1791417578e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.