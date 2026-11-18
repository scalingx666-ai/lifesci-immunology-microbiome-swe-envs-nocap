# Issue

**Title:** Simplify state and transition labels in Graphviz display

## Description

IMO, given that the state vs transition distinction is captured by both the shape and color of the nodes, it isn't necessary to prepend "S_" and "T_" to the labels.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a35b4e90ad10`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.