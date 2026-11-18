# Issue

**Title:** Bugfix/seq info mode no match

## Description

- fix #192 when accession2seqid files were empty, breaking the seqinfo data
- also fixed the filtering of accessions without taxid from accession2seqid files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1a9b8af1b2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.