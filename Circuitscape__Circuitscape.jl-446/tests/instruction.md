# Issue

**Title:** Replace Dict{String,String} config with typed CSConfig struct

## Description

## Summary

Depends on #444 (pardiso-extension).

- Replace `Dict{String,String}` config with a typed `CSConfig` struct (49 fields with proper Bool/enum/Int/String types)
- Eliminates string parsing in hot paths — `cfg["suppress_messages"] in TRUELIST` becomes `cfg.suppress_messages` (direct Bool access)
- Full backward compatibility: `compute(dict::Dict)` and `init_config()` still work

## What changed

- New `CSConfig` struct with `@kwdef` and 6 enums (`DataType`, `Scenario`, `SolverType`, `Precision`, `LogLevel`, `RemovePolicy`)
- `CSConfig(::Dict{String,String})` constructor for backward compat
- `parse_config` now returns `CSConfig`
- ~80 `cfg["..."] in TRUELIST` / `cfg["..."]` sites replaced with direct field access across 13 files
- `compute_omniscape_current` still accepts `Dict{String,String}`, converts internally
- `init_config()` still returns `Dict{String,String}` for Omniscape.jl compat

## Backward compatibility

- `compute("path/to/file.ini")` — works as before
- `compute(dict)` where dict is `Dict{String,String}` — works, converts at boundary
- `init_config()` — still returns Dict
- INI file format — unchanged

## Test plan

- [x] All 719 tests pass
- [x] CI passes on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93243113774a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.