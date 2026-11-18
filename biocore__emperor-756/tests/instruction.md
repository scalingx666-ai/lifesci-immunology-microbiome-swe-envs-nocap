# Issue

**Title:** BUG: Fixes bug creating SVG legend

## Description

The code was using the old way to access grid data. I looked in the rest
of the codebase and there checked there aren't any other usages of
getData (only when necessary).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6663883bc55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.