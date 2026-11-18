# Issue

**Title:** substantial Snakefile cleanup

## Description

This PR cleans up the spacegraphcats snakemake Snakefile --

* switch to using f-strings in place of expand, os.path.join, etc.
* simplify bcalm so that output will be logged properly (I hope)
* fix indenting in several places
* switch to using input and output keys instead of indices

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dc15d172b01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.