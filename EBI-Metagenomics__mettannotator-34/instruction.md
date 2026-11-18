# Issue

**Title:** Fast mode nextflow changes

## Description

It also includes a change on the LOOKUP_KINGDOM process, instead of using the filename to get the kingdom it uses the nextflow process output > env to get the value.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df07f715336b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.