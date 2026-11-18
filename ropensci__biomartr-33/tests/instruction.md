# Issue

**Title:** Use stringr::str_to_title() for Ensembl filenames

## Description

Ensembl capitalizes the genus in the filenames on their FTP site, requiring str_to_title() to fix the name.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97249c9a97a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.