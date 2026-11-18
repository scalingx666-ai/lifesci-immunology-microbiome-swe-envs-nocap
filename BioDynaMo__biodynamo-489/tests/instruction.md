# Issue

**Title:** Fix bdm view launching ParaView from the wrong directory

## Description

Track whether each state file was discovered under output or build/output. Use that information to choose the working directory instead of searching the full path for the substring build.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f14cf98fc8c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.