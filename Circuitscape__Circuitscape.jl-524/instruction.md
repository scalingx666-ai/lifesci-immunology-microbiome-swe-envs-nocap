# Issue

**Title:** Match Circuitscape 4 source strengths and excluded points in one-to-all modes

## Description

Part of the parity review against Circuitscape 4.0.5.

## Summary
- **Variable source strengths are looked up by focal id**, with default 1 when an id is absent, as Python's `get_strengths_rc` does. Previously the one-to-all strength came from row i of the file for the i-th unique point and the all-to-one strength map was indexed by row of the point list, so an unsorted file applied strengths to the wrong points and a missing id threw. A new `read_variable_strengths` reads the raster strength file without the network 0-based shift and validates two columns.
- **All-to-one with included pairs**: the source map is masked by the pruned point map, so excluded focal points inject no current, with unit or variable strengths. With variable strengths this deliberately deviates from Python 4.0.5, which zeroes an excluded point's id before the strength lookup and so still injects 1 A there (a CS4 bug). The `allToOneVerify12` reference current maps encoded that bug and are regenerated; each new map equals a run with the excluded points removed. Noted in `migration.md` under "Changed results".
- The nothing-to-solve test now matches Python's intent, including a lone multi-cell region, and a focal voltage of exactly zero is reported as is rather than mapped to −1.

## Test plan
- [x] New testsets: oneToAllVerify12 with a reordered strengths file, a dropped id, and an id-0 row all reproduce the reference resistances; all-to-one with a reordered file reproduces the reference cumulative map; a synthetic all-to-one case where an excluded point gives the same current map as omitting the point.
- [x] Full `Pkg.test()` passes; the only reference outputs changed are `allToOneVerify12` current maps (see above).

## Review
See the review comment for the per-item CS4-vs-CS5 determination and follow-up commits 03e15ef, b5b45e6.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382cc4676892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.