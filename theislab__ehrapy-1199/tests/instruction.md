# Issue

**Title:** Bump the tutorials to the data tutorial and ehrdata to 27b663a

## Description

Adds the data tutorial as the first tutorial in place of ehrapy_introduction, with a redirect from its old URL, and moves ehrdata to the main branch with the new real datasets it needs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01b210e4985b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.