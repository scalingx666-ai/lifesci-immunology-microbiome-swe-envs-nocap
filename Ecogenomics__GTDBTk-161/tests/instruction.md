# Issue

**Title:** Supply genomes as called genes

## Description

* --genes parameter indicates that the directory contains amino acids
* typically usage will require -x faa or files won't be found
*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `120d743952f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.