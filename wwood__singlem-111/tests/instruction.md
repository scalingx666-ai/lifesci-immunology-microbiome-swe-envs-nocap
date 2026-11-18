# Issue

**Title:** Query: add coverage to output

## Description

- [x] Get test_makedb_and_query.py passing
  - [x] Fix test_limit_per_sequence (unlimited output is now huge)
- [x] Add coverage to output in query_formatters.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4c9be0d92a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.