# Issue

**Title:** Fixing directory cocatenation for empty KINSTALL

## Description

I ignored that `$KINSTALL` also should work when empty, which causes errors in this case. I reverted this and added a conditional check for a missing trailing slash instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5bf129ee219`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.