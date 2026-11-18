# Issue

**Title:** Test recovery from a missing ParaView plugin handler

## Description

Add a fresh-process regression test covering a cached missing handler, disabled visualization, unknown adaptors, and repeated construction. Correct the visualization-selection test friend declaration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec3cfa4f4014`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.