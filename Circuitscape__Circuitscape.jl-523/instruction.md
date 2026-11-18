# Issue

**Title:** Match Circuitscape 4 graph construction over polygons and nodata

## Description

Part of the parity review against Circuitscape 4.0.5. Builds on #520.

## Summary
- **Polygons over nodata no longer create edges.** Both ports give every polygon cell the polygon's node id, including nodata cells, but Python connects two cells only when both have nonzero conductance. `construct_graph` and `count_graph_edges` now require that as well. Under the default conductance averaging a nodata cell inside a polygon used to be joined to its habitat neighbours with weight g/2.
- **One-to-all focal regions overlapping a polygon** become one node with every polygon they touch, following Python's `get_poly_map_temp`: for each point id in sorted order, a fresh id is given to the overlapped polygons on the running map and to all of the region's cells. Previously the region was split into two nodes, and a polygon elsewhere whose id equalled the point id was merged in.
- **Negative habitat values are clamped to zero conductance** after conversion, as Python does, so they are null for the graph, for polygons, and for the null-to-nodata output options. A warning reports how many cells were clamped.
- **Edges require positive conductance** on both cells (one `_linked` predicate shared by `construct_graph` and `count_graph_edges`), so in-memory -9999/NaN cells inside a polygon get no edges.
- The focal-region merge runs in linear time (union-find) and `create_new_polymap` is type-stable again.

## Fixture check
19 fixtures have polygon cells over nodata and lose between 1 and 11 edges. All 19 were run on master and on this branch, 236 output files compared, max absolute difference 0. The removed edges were self-loops within a polygon or had zero weight under resistance averaging; no fixture exercises the spurious g/2 edge with conductance averaging, so no reference output changed.

The `oneToAllVerify11` `create_new_polymap` unit test expectation is updated to Python's label values; the grouping of cells into nodes is identical.

## Test plan
- [x] Three new testsets (47 assertions): the point-map form of `create_new_polymap`, polygons over nodata in all four averaging and neighbour modes with edge-count consistency, and negative cell clamping.
- [x] Full `Pkg.test()` passes.

## Review
See the review comment for the per-item CS4-vs-CS5 determination and follow-up commit 28a1551.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382cc4676892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.