# Issue

**Title:** Support for 'descriptions' in pan-graph-db files

## Description

Most anvi'o dbs have 'description' key in their `self` tables that enable users to add markdown-formatted free text into dbs for downstream use.

This PR enables pan-graph-dbs to benefit from the same functionality.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e44bfeab8621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.