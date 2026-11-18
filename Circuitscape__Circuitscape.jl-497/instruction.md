# Issue

**Title:** Index network branches once so cumulative currents accumulate in O(E)

## Description

The last significant lock-related cost in the core path, found while auditing locks after #492.

## The problem
In network pairwise mode with current maps, accumulating a pair's branch currents into the cumulative vector located each branch's slot with `findfirst(isequal((i,j)), coords)` — a linear scan over all E edges, tried in both orientations — so each pair cost **O(E²)**, and it ran *inside* `cum.lock`, serialising every thread's postprocessing behind it. Nobody had hit it hard only because large networks with per-pair maps are uncommon.

## The fix
`Cumulative` gains `branch_index::Dict{Tuple{V,V},Int}`, built once in `initialize_cum_vectors` with both orientations of every edge mapped to its slot (first occurrence wins for a duplicated edge, exactly as the scan did). Slots are resolved **before** taking the lock, so the critical section shrinks to the adds themselves. The raster constructor gets an empty dict; the field is unused there.

## Measured (ring network, 1 pair, `write_cur_maps = True`, best after warm-up)
| edges | before | after |
|---|---|---|
| 2,000 | 0.01 s | 0.01 s |
| 20,000 | 0.21 s | 0.07 s |
| 60,000 | 1.36 s | **0.19 s** |

Before: ×3 edges → ×6.5 time (quadratic). After: ×2.7 (linear; the remainder is the solve and file write). Per pair, so a 60k-edge network with 1,000 pairs was spending ~23 minutes scanning.

## Tests
The network pairwise gold files include the cumulative branch and node current outputs (`*_branch_currents_cum.txt`, `*_node_currents_cum.txt`), which pass unchanged. Full suite: Unit 484/484, CG+AMG and CHOLMOD × Float64/Float32 685/685 (fast path), Issue 341 46/46.

Independent of #496 (different files).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08c801bc5422`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.