# Issue

**Title:** fix #3219

## Description

To my knowledge, this appears to fix the outstanding issue. Validation of the two required fields is handled by bootstrap and jinja2. Unselected pulldowns will now display a default tool-tip bubble.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aac0ec7c239d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.