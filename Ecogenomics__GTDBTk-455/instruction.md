# Issue

**Title:** refactor(Fix issue #448): Refactor code to return warning instead of …

## Description

…crashing

when all the genomes are filtered out and not classified. GTDB-Tk now returns an error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bf35e79276f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.