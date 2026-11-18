# Issue

**Title:** Improve GHA

## Description

Old GHA build docker image 2 times and thus used excessive memory. This lead to error. "System.IO.IOException: No space left on device :" in GHA run.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `492b48219b96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.