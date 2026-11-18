# Issue

**Title:** Debug/virify qc

## Description

Virify predictions are now visible in the final GFF3 file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fec6450db53b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.