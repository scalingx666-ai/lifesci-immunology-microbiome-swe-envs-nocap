# Issue

**Title:** fix multiple singletons and singleton-first issues in prep_icar_data

## Description

allows prep_icar_data to deal with multiple singletons in a connectivity matrix regardless of position

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55527969b62f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.