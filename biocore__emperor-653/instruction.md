# Issue

**Title:** BUG: Refresh button state

## Description

According to the documentation[1], the UI has to be manually refreshed
after changes to a button's state.

[1] - http://api.jqueryui.com/button/ see the refresh() section

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9bf6c8d17f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.