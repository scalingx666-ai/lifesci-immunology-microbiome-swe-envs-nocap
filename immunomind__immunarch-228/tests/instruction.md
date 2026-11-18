# Issue

**Title:** BCR updates and hotfixes

## Description

* MiXCR parser updated: loading 3'V and 3'J deletions/insertions into table
* repGermline: use only first reference sequence by default (instead of all possible options)
* repGermline: bugfix for V/J trimming in germline
* repAlignLineage: data only required for Phylip is in the output by default

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d7fcc422de2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.