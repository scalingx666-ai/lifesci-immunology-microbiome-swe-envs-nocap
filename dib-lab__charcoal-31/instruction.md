# Issue

**Title:** adjust thresholds after inspection

## Description

* gather decontam now requires minimum of 3 hashes (3kb at scaled=1000) to remove contig

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `63396705ec6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.