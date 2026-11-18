# Issue

**Title:** Slightly clean up concatenate script

## Description

* Add automatic help, which is more robust
* Normalize path before checking parent to address edge cases like "a/"
* Correctly close file handles on exception

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26df8cda5bfa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.