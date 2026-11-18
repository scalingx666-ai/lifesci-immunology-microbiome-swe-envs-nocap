# Issue

**Title:** Hot fix/genomad empty input

## Description

Modules update to fix integronfinder reporting negative coordinates as reported in  and .
Other tools were updated as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1cde66b8f914`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.