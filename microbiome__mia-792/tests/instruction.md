# Issue

**Title:** Fix typos in documentation for Double Principal Correspondence analysis: "Correspondance" → "Correspondence"

## Description

This pull request corrects a spelling mistake in two files:

- `R/runDPCoA.R`
- `man/runDPCoA.Rd`

The word "Correspondance" has been replaced with the correct spelling "Correspondence".

No functional changes; documentation fix only.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b23983df10b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.