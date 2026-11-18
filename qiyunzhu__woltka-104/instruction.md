# Issue

**Title:** renamed gOTU with OGU

## Description

And removed the "gotu" command since it is identical to "classify" without parameters.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cb3ac61d4c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.