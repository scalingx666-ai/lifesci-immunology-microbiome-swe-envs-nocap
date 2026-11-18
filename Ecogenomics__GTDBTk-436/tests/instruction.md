# Issue

**Title:** Update tigrfam_search.py

## Description

Adding 'stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL' to fix issue #420.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a932df1f429`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.