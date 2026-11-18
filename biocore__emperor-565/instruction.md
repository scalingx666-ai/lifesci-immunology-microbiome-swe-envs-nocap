# Issue

**Title:** ENH: Remove the requirement to shift+right click

## Description

The plot's context menu is now shown without the need of holding shift
and right-clicking. With this patch, the user will need to *only* right
click to show the context menu.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88ca8abd8409`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.