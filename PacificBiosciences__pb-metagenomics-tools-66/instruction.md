# Issue

**Title:** diamond-megan update

## Description

Created separate environments for rules to prevent bad env recipes. 
Added `Snakefile-diamond-megan-ue.smk` to allow access to KEGG annotations with MEGAN-UE.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd7db2215295`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.