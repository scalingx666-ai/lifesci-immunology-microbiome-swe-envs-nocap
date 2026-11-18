# Issue

**Title:** Refactor extract_nodes_by_query, rename to query by sequence

## Description

Goal: clean up the frontier search code so that it actually makes sense and is understandable!

Note: search output on dory-test and twofoo is identical.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19685de77912`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.