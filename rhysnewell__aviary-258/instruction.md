# Issue

**Title:** Remove mamba

## Description

Currently on top of #256 and #257, too lazy to be independent but could later if required.

This is backwards incompatible because the command line option is removed. We could keep it but ignore it and always use conda instead of the (now deprecated) mamba?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e123cdebe8a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.