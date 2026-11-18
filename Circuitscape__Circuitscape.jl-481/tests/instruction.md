# Issue

**Title:** Look excluded pairs up in a Set in the pairwise solvers

## Description

, which fixed this on the raster polygon path only.

In include mode `exclude_pairs` holds nearly every combination of focal nodes in both orders (~P² entries), and both `solve` methods scanned it linearly once per candidate pair — in `get_num_pairs` and again inside the solve loop — so the bookkeeping is O(P⁴) before a single system is solved.

Measured on master at the scale in #341 (292 focal nodes, 3 included pairs, one 200k-node component):

| | time |
|---|---|
| exclude scans, `Vector` | **1.389 s** |
| exclude scans, `Set` | 0.009 s |

Two lines: convert once where `prob.exclude_pairs` is read. `in`, `∉` and `isempty` all work unchanged; both orders are already present in the list so membership semantics are identical.

Full suite passes locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ba96dc13825`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.