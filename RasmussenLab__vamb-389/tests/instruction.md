# Issue

**Title:** Mask short contigs when loading TSV abundance

## Description

Previously, the TSV file was expected to only contain the retained contigs. This is confusing for users, since they natually assume the TSV file should contain the same contigs as the composition or the FASTA file. So, also mask the TSV file with the composition metadata mask when loading it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fa32805d726`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.