# Issue

**Title:** Fix/user mobilome clean

## Description

The `user_mobilome_clean.gff` output is now generated and includes an extra key in the attributes column to label the type of MGE the CDS belongs to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `123688726d7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.