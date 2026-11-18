# Issue

**Title:** Add git-blame-ignore-revs

## Description

These commits have been code formatting changes which pollute the history.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5389c1bdf9e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.