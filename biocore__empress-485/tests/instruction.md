# Issue

**Title:** Fixes error when no feature metadata file is provided

## Description

When I previously ran empress without supplying a feature metadata file, I received the error "All objects passed were None." This occurs on line 167 when pandas attempts to concatenate two Nones. I added a line to check whether both self.tip_md and self.int_md are both None to avoid raising the error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d14e07d7477`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.