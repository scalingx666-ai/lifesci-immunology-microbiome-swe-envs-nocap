# Issue

**Title:** Document all INI arguments with defaults and types

## Description

## Summary
- Add complete INI Argument Reference table to `docs/src/options.md` covering all ~49 config parameters
- Organized by section with argument name, type, default value, and description
- Unimplemented features (`set_focal_node_currents_to_zero`, `use_reclass_table`) are noted
- Fix bug in `write_config()` where `polygon_file` was written as `cfg["use_polygons"]` instead of `cfg["polygon_file"]`

## Test plan
- [x] Docs build successfully
- [x] All arguments cross-checked against `src/config.jl`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a52c991a6bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.