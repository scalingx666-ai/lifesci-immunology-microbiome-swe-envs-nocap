# Issue

**Title:** Major revision for bug fixes and generalization of whole package

## Description

As specified on email, some fixes still remain, and I do believe there still is a bug on windows for URL checkers, also
the new ensemble collection file storage system for metazoa is still not working.

One of the major goals will be to remove hard coded URLs and error messages and generalize these into functions, so the whole package will be much cleaner to fix in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac010ee52453`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.