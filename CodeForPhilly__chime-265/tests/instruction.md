# Issue

**Title:** Warnings if infection counts incorrect

## Description

Added in-line warnings if the number of estimated infections is greater than the regional population, or if known infections exceed estimated infections. This is a rough draft - still need to work out text placement, text style, and confirm that warnings are displaying under the correct conditions.

Fixes: #264

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `477d139319fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.