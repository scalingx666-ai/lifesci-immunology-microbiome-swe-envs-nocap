# Issue

**Title:** allow artifact summary update

## Description

This will allow us to update artifact summaries via: `artifact_summary_post_request(user, artifact_id, force_creation=True)` and while adding this, I realized that we were removing the current file if the file had the same name that the previous version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60f3cc1eb9da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.