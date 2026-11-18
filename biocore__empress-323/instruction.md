# Issue

**Title:** Fixes #317

## Description

and uses `biom.Table` rather than `pd.DataFrame` for the feature table

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3ed544cbab8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.