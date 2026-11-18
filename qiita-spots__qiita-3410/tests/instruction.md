# Issue

**Title:** Fix msg admin none

## Description

Once in a while when an admin job doesn't have a message yet (cause it's None), the GUI will brake cause it can do the str.replace; this is a small fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55e460e9ae8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.