# Issue

**Title:** Adding minimums to prevent UI crash on validation/divide by 0 errors …

## Description

…()

Noticed that most of these crashes were due to an uncaught validation (seems like it was everything in the Severity Parameters section) or a divide by 0 error. As a patch, suggesting just having the UI enforce minimums to prevent the user from violating one of the validation policies. Thoughts?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90998add4dbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.