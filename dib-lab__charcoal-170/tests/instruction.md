# Issue

**Title:** [WIP] fix a few things in the demo

## Description

This PR updates charcoal with two fixes -

* first, a weird interaction between `ancient` and the genome info file(s).
* second, properly update to GTDB release 95, which I think will fix #169 (which seems to boil down to accession number problems, after all the other work @edgraham did!)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4653b312446`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.