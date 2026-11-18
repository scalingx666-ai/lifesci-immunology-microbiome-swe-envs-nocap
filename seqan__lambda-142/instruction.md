# Issue

**Title:** [Fix] get correct ref names for sam/bam output

## Description

Former version had some problems:
1) Resize followed by append results in empty reference names in sam output as first n names are empty strings 
2) Iterating through substring appends single characters to stringset

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `769058d1498b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.