# Issue

**Title:** import functions and ranks

## Description

importBIOM did not detect superkingdom rank. Also it was not possible to set taxonomy ranks automatically. These issues are now fixed.

Also, the supported ranks come from generic function to ensure that support can be extended easily in every function at once.

This is a draft, still checks to do.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bea08516b5a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.