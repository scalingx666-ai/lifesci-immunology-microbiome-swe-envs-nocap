# Issue

**Title:** Fasta IDs renaming fixed

## Description

A couple of fixes in the scripts that were modifying the headers. Also there was an error in the gff-writer scripting the step of fixing the CDS coordinates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2fa9676d00a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.