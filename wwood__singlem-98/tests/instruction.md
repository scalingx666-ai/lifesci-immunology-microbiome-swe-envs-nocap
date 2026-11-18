# Issue

**Title:** Enable processing of tree-less GraftM packages, fix premature taxonomy hash deletion

## Description

Addresses #97 

Also fixes a bug where the taxonomy hash pickle is deleted before the final spkg is compiled.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e4e63b8cfd5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.