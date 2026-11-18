# Issue

**Title:** Bugfix/gtdb metadata url

## Description

Fix changes in metadata files from GTDB (`.tar.gz` with one .tsv file inside to compressed tsv `.tsv.gz`):
- `ar53_metadata.tar.gz` -> `ar53_metadata.tsv.gz`
- `bac120_metadata.tar.gz` -> `bac120_metadata.tsv.gz`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `262c2558c596`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.