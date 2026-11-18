# Issue

**Title:** add dependency for rule hashval_query

## Description

rule hashval_query was missing the input file for 'catlas.csv', causing the rule to break from missing file. See comments on #233

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80960a585d83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.