# Issue

**Title:** Match Circuitscape 4 network input handling

## Description

Part of the parity review against Circuitscape 4.0.5.

## Summary
- **Focal node numbering.** `read_focal_points` now receives the zero-based flag from `load_graph` and shifts only when the graph was shifted, instead of guessing from whether the focal list happens to contain node 0. A zero-based chain 0–1–2–3 (1, 2, 3 Ω) with focal file `1,3` now gives 5 Ω as Python does; it gave 3 Ω before. The list is also sorted and deduplicated as Python's `np.unique` does.
- **Reclass tables in network mode** are applied to edge values before the resistance-to-conductance conversion, as CS4 does. The table stays a single lookup (CS5 behaviour, documented since v6): CS4's sequential row application makes chained rows compound in an order-dependent way, which #231 identified as a bug, so it is deliberately not reproduced.
- **Zero resistance edges** raise a clear `ArgumentError` instead of dying inside LAPACK.
- **Edge lists** accept `#` comment lines and comma delimiters, and reject files with fewer than three columns.
- **Sources or grounds at ids not in the graph** are skipped with a warning instead of a `BoundsError`.
- **Source/ground ids shift only with the graph.** `read_point_strengths` no longer infers a 0-based shift from a 0 in the list, which moved every source on a 1-based graph to the wrong node.
- **Edge list as focal file**: only the two node columns are read, as CS4 `read_focal_nodes` does.

## Test plan
- [x] New "Network I/O matches Circuitscape 4" testset (20 assertions) covering all five items with temp files.
- [x] Full `Pkg.test()` passes; no network fixture result changed.

## Review
See the review comment for the per-item CS4-vs-CS5 determination and the follow-up commit b52c5c8.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b34a36be3102`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.