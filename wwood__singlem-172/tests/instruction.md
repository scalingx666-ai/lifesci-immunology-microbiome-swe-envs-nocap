# Issue

**Title:** Update to metapackage v5

## Description

Features the following:
- Implementation of metapackage-specific parameters for DIAMOND prefilter and DIAMOND taxonomy assignment
- Sensitivity customizability of the metapackage DIAMOND prefilter database
- Taxonomy database name and version keys

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a70d078bf7f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.