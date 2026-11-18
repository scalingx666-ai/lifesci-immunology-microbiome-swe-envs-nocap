# Issue

**Title:** ENH: Save mapping file and coordinates as JSON

## Description

The data is now written using JINJA's tojson filter, this makes the
translation a bit more natural, specially for numbers in scientific
notation.

You may need to update jinja or you might get an error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15c9885823d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.