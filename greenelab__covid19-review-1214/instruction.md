# Issue

**Title:** Update rootstock on 2024-01-14

## Description

Needed to resolve Manubot build errors. I did not include the updates to support Mastodon because our front matter is already customized.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26d9bf150181`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.