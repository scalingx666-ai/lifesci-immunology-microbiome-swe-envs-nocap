# Issue

**Title:** curatedMetagenomicData script: fix colname shift, take no arguments, …

## Description

…take "-l --list" argument.

script and R/ExpressionSet2phyloseq.R: divide reads by 100 for counts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b25e978bd2d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.