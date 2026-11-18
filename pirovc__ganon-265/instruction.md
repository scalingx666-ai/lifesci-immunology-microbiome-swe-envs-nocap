# Issue

**Title:** Bugfix/target node tax

## Description

add verification for the bug reported in #264 and additionally uses the add method from multitax, which would fail in the bug reported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `199281f8d7d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.