# Issue

**Title:** Match Circuitscape 4 conflict handling in advanced mode

## Description

Part of the parity review against Circuitscape 4.0.5.

## Summary
- **Read-time conflict pass for rasters.** `read_source_and_ground_maps` now resolves source/ground conflicts on the cell maps after unit currents and direct grounds are applied, as `csio.py` does: `rmvsrc`/`rmvall` zero conflicting sources, `rmvgnd`/`rmvall` zero conflicting grounds, and an empty map raises "No valid sources/grounds detected". Previously `rmvall` removed only sources, and under `rmvgnd` a finite ground at a conflict cell stayed on the diagonal because finite grounds were computed before the policy applied. The node-level pass in `advanced.jl` deliberately deviates from Python's: `rmvall` removes both source and ground, and finite grounds are taken after resolution so `rmvgnd` really removes the ground (Python's `compute.resolve_conflicts` has both bugs, visible for networks and polygon-merged cells).
- **Components with sources summing to zero** are solved: the skip test counts nonzeros instead of summing, so +1 and −1 sources in one component no longer skip.
- **Nothing to solve** follows Python in advanced mode: a component with no nonzero source or ground is skipped, while a component whose resolution removed all of one raises. One-to-all / all-to-one keep the CS5 behaviour of reporting `-1` for such a focal node rather than aborting the run. `compute_omniscape_current` opts out of that error and keeps returning a zero map, since its moving-window loop depends on it.
- **Network `fill_sources_and_grounds!`** no longer inverts `ground_map` in place, so building a problem twice from one `NetworkData` gives the same grounds.

On the 5x5 review case (source and finite ground on one cell), `rmvgnd` and `rmvall` voltages previously differed from the Python-order result by 2.30 V and 1.10 V; both are now identical.

## Test plan
- [x] New "advanced conflict policies" testset (21 assertions): all four policies on a 3x3 conflict, the empty-map errors, the all-conflicted error, ±1 sources, network double-build.
- [x] Full `Pkg.test()` passes; no advanced-mode fixture output changed.

## Review
See the review comment for the per-item CS4-vs-CS5 determination and follow-up commit 1245439.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382cc4676892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.