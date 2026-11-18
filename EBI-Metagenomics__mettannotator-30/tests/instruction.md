# Issue

**Title:** Bugfix/unifire inputs

## Description

- a bugfix for UniFIRE to correctly handle cases when the ARBA predictions file has 6 fields
- UniFIRE fails to parse files with quotes in descriptions; added removal of special characters to get around this

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e079e76d2a7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.