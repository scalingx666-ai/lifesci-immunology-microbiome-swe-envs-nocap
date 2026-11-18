# Issue

**Title:** Fix focal regions overlapping polygons in create_new_polymap

## Description

## Summary
In pairwise mode with focal regions (a point id spanning several cells), `create_new_polymap` builds the polygon map that collapses the two regions being solved into nodes. Two branches were wrong since the 2017 port:

- **Region overlaps exactly one polygon cell**: read `overlap`, which is only defined in the other branch, so the run threw `UndefVarError`.
- **Region overlaps several polygons**: relabelled the polygons but never labelled the region's own cells that lie on no polygon, leaving them as separate nodes outside the focal node.

Both now follow Circuitscape 4's `get_overlap_polymap`: every polygon the region touches and every cell of the region get one new id. The overlap is detected on the map already updated for the first region, so two regions sharing a polygon collapse into one node, as in the original.

Four unit tests cover no overlap, single overlap, multiple overlap with a non-polygon cell, and two regions sharing a polygon.

## Test plan
- [x] `Pkg.test()` with 4 threads: all suites pass against the reference outputs, so no existing verification case exercised the changed branches.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ed921d95e40`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.