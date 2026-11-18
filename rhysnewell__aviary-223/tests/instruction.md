# Issue

**Title:** assemble/recover: Require users to specify coassembly or not.

## Description

.

This is a breaking change for the command line (before it would silently not coassemble), but the break will cause an error to be thrown at least. I guess there are documention fixes to be done too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37f8bd1a4f3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.