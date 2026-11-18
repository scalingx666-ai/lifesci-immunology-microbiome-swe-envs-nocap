# Issue

**Title:** Update rootstock on 2021-06-11

## Description

We updated to Pandoc 2.12 to support LaTeX export.  However, that broke some Manubot formatting.  Rootstock now supports the latest Pandoc, so this will fix some of the minor issues introduced with our prior Pandoc update.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `176c0946a924`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.