# Issue

**Title:** cleanup!: drop support for julia <1.9 and remove requires

## Description

This is paving the way for the upcoming v0.9 release along with Catlab v0.15 which will remove Julia <v1.9 support so we are following along with that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6a4cf295569`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.