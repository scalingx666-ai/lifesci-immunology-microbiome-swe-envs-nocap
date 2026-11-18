# Issue

**Title:** Schedule weekly build in CircleCI

## Description

This is a change to the test configuration only, to schedule an automatic weekly build in CircleCI for dev and stable.  I figure this should help us catch dependency/version-related problems even if we haven't changed anything lately.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b861daceb3c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.