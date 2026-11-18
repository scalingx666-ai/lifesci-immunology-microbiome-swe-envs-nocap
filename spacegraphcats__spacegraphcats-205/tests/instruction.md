# Issue

**Title:** Determ. iteration in domination_graph

## Description

We still have non-determinism inside the graph data structure, but this one point is where I suspect results might change substantially depending on iteration order. If this does not help to normalize results we need to introduce ordered sets in graph.py.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96bb41fea2f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.