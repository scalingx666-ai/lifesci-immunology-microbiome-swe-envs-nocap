# Issue

**Title:** Add handling for unhealthy connections via new methods/"constructors"

## Description

This can hook up disconnect/reconnect errors to a new error handler.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf70885feba9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.