# Issue

**Title:** ci: prepare for merge queue

## Description

Prepare for merge queues:
https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue#triggering-merge-group-checks-with-github-actions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71dcd491dd24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.