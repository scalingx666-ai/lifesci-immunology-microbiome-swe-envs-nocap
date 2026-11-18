# Issue

**Title:** Reachable nodes

## Description

Export 3 new functions:
- `get_forward_reachable` 
- `get_backward_reachable`
- `as_cumulative_edgelist.networkDynamic`

They compute the set forward and backward reachable from a subset of nodes in a dynamic network represented in a cumulative edgelist.

These functions are time and memory efficient versions of `tsna::tPath` for multiple nodes and when the only information of interest is the presence or absent of a node in the reachable set over a time period.

`get_backward_reachable` is only a wrapper around `get_forward_reachable` where the edges times have been inverted (`head = -tail` and `tail = -head`)

`as_cumulative_edgelist.networkDynamic` returns a cumulative edgelist representation of a `networkDynamic` object. This representation is lightweight and formatted similar to the other cumulative edgelists uses all over `EpiModel`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2bd6918e33d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.