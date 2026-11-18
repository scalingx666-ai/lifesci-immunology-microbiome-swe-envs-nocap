# Issue

**Title:** CAtlas indexing and isolate removal

## Description

This  by letting level 1 be the leaves rather than level 0.  It also does not propagate up the CAtlas nodes corresponding to components that are simply isolated vertices.  Instead, once a vertex becomes isolated in the domgraph, its corresponding CAtlas node immediately becomes a child of the root.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0905de356bc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.