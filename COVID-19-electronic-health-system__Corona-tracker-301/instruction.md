# Issue

**Title:** Used useHistory to redirect to health log on survey submission

## Description

## Changes
- as title states, we're not using `window.location.reload()` anymore, as that breaks the authentication and will not work in production

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f48b888726ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.