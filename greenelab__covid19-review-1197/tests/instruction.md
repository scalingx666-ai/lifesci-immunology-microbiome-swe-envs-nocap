# Issue

**Title:** Update owiddata-stats.json

## Description

Out external resources builds stopped working so this is a temporary workaround to try to fix the broken figures in the manuscript. #1196 fixed the code but not the output files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `080dff7b428d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.