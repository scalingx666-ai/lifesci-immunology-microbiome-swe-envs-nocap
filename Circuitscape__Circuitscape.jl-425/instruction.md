# Issue

**Title:** Update Project.toml

## Description

32-bit solving needs Julia 1.11, but otherwise Julia 1.6 should be fine.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a27fb571a83c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.