# Issue

**Title:** feat: use equality for xnor operation on booleans

## Description

Instead of manually checking if a record passes a filter and the corresponding filter attribute was set to true or the contrapositive of that, we can just use the equality (xnor) operator.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b061ceed6b1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.