# Issue

**Title:** Update nginx_example.conf

## Description

Elaborate on reason for 7M as client_max_body_size, although it is configured as 3*1024*1024.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4cef03a82946`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.