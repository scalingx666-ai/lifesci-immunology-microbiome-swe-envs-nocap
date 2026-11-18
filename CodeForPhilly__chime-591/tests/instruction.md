# Issue

**Title:** Perform kubectl diff against correct environment when staging deployment

## Description

- Prod deployment was erroneously performing
 diff against preprod environment (#590)
- Bump kubectl version to 1.18.2 to resolve
 catastrophic bug ()

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac5bf09cd71e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.