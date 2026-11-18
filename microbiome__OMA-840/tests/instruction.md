# Issue

**Title:** refactor: switch style workflow to use git-auto-commit

## Description

Use [this action](https://github.com/stefanzweifel/git-auto-commit-action) now
instead of custom script.

Also upgraded checkout Action to v6, and did some yaml styling.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc357324ace0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.