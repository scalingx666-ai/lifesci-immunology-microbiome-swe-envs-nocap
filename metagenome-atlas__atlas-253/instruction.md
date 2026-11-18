# Issue

**Title:** Mem

## Description

I changed the config file argument `java_mem` to `mem` but didn't change id consistently throughout my code.  This PR solves this problem.  

This is probably a source of error for #229.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59da38f63bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.