# Issue

**Title:** Saving inserted mutations/sequencing errors to a vcf file

## Description

The final feature that was requested is a record of all the sequencing errors that have been added to the reads during the simulation. I have made a new parameter that enables outputting these "mutations" to a VCF file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb425d15387b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.