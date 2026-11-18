# Issue

**Title:** ENH: Adds changes to support standalone plots

## Description

We now have a template that lets you create standalone plots, similar to the
ones that ./build.py would create, instead this time it is part of the main
Emperor API.

I've added the necessary tests, and updated where appropriate.  These changes
are needed to create the Emperor plugin for QIIME 2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1853d1d0c05c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.