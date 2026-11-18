# Issue

**Title:** refactor: use iterator's position method to find first index of occurrence

## Description

### Changes
- Removes manual implementation of finding first index.
- Replaces all occurrences of `find_first` with the position method of iterators. 

Tests are passing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `593d1a2a5378`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.