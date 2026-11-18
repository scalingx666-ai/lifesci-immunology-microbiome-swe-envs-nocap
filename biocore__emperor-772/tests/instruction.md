# Issue

**Title:** BUG: Update controller properties

## Description

Some defaults changed in the most recent version of THREE.js. These were
preventing panning around with scatter plots. I also cleaned up some
additional code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c1f61652913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.