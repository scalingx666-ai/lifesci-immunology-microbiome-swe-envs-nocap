# Issue

**Title:** Fix included pairs file being ignored

## Description

## Summary

The `included_pairs_file` / `use_included_pairs` feature has been broken since the Julia rewrite. Include/exclude pairs files were silently ignored — all pairs were solved regardless.

## Root cause

`generate_exclude_pairs` returned matrix position indices (1, 2, 3...) but the solver comparison sites used user-facing node IDs from the input file. Since these are different number spaces, the exclude check almost never matched, and all pairs were computed.

Multiple users have reported this issue since 2022.

## Fix

- `generate_exclude_pairs` now returns node ID pairs (matching the Python v4 behavior)
- The solver converts exclude pairs from node IDs to graph node indices at the boundary
- The polygon path comparison already uses node IDs and works correctly with this change

## Test plan

- [ ] Verify with a 3-node test: include only pair (1,2), confirm pairs (1,3) and (2,3) show -1 resistance
- [ ] All existing tests pass
- [ ] CI passes

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36052945b681`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.