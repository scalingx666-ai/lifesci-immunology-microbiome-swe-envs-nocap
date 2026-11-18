# Issue

**Title:** getHierarchyTree: empty cells

## Description

I noticed that only NA cells were considered as empty. This led to error --> the created tree was not matching with rows if cells contained for instance character "".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58ac212bda4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.