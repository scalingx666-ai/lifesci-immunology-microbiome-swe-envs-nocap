# Issue

**Title:** Add SKIP_ORF option in translated_search

## Description

added a new parameter, and changed **translated_search.sh** to run _extractframes_ and _translatenucs_ instead of _extractorf_ according to the user's choice

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88d102d976a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.