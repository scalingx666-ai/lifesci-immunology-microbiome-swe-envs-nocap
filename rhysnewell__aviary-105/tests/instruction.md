# Issue

**Title:** Fix checkm subprocess

## Description

The command can fail with "No such file or directory" if the database path uses shell stuff.
Could open an injection vulnerability.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `520dedde83d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.