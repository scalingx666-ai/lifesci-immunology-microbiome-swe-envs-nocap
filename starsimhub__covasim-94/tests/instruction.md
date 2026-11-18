# Issue

**Title:** Relative susceptibility

## Description

Add new parameter to `Person` - susceptibility. Now we can modify each person chances to get infected. For example doctor without PPE would be much higher than paranoid person wearing mask to grocery store.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98e4071d9a9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.