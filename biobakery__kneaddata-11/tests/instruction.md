# Issue

**Title:** Changed bowtie2 setting and removed spaces identifiers

## Description

* Trim the spaces in the identifiers sequences of the input files
* Bowtie2 default options set to --very-sensitive-local

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebed9747e619`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.