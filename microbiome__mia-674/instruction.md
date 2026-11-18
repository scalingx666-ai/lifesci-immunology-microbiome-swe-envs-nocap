# Issue

**Title:** Install phyloseq from Bioconductor

## Description

Related to this PR: 

phyloseq in Bioc devel is failing to build which makes our build to fail (we have phyloseq as suggested package, and it is used in examples). Currently, it is installed from GH, but this should be changed back when phyloseq is fixed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1aa5455df4c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.