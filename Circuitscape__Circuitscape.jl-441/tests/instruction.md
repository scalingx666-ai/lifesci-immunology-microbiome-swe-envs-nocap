# Issue

**Title:** Don't write cumulative current map when write_cur_maps is False

## Description

## Summary
- Guard `write_cum_maps` calls in both pairwise paths (with/without polygons) so cumulative maps are only written when `write_cur_maps` or `write_cum_cur_map_only` is `True`
- Fix the same missing `write_cum_cur_map_only` guard in `onetoall.jl`
- Add test verifying no `cum_curmap.asc` file is produced when `write_cur_maps=False`

Previously a cumulative current map filled with zeros was always written to disk in pairwise mode.

## Test plan
- [x] Existing 719 tests pass
- [x] New test: verify no cumulative map file when `write_cur_maps=False` (uses existing test case 12)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94811a50835b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.