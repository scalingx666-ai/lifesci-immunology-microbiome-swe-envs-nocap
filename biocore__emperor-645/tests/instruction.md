# Issue

**Title:** BUG: Fix problem with double-click resize

## Description

Resizing the menu would erroneously be triggered by double-clicking the
menu, whereas it should only be triggered when double-clicking the
resize handle.

This had previously been reported by @wasade and a few others.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45b1437c9e5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.