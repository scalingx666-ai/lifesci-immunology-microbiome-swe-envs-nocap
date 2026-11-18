# Issue

**Title:** Workplace changes to match Python 3

## Description

A couple notes.

First, seems like my editor doesn't like trailing whitespace, so its cleaned up a lot of that in the files.

Second, there are a few Python 3 changes (mostly to FARZ.py but two to extended_models.py). 

Third, adding some helper functions for re-drawing basic parameters from gamma distributions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7badfd5f83c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.