# Issue

**Title:** Validate configuration before reading any data

## Description

Closes the root of several recurring issue themes (#246, #341, #360, #366, #397, #412, #433, #436): options that were silently ignored or silently defaulted, and file errors that surfaced deep in a load path with a message that did not name the INI key.

## Strict parsing
Every enum-valued option (`solver`, `scenario`, `data_type`, `precision`, `log_level`, `remove_src_or_gnd`) and every boolean now rejects values it does not recognise, naming the key and listing the valid values, instead of falling back to a default. On master `solver = cholmodd` ran cg+amg, `scenario = pairwsie` ran pairwise, `write_cur_maps = Ture` wrote nothing. A missing `scenario` is an error rather than an implicit pairwise. Unknown keys are warned about (not fatal — legacy Python keys like `print_timings` are in the default set and stay silent).

Circuitscape 4 wrote `remove_src_or_gnd = not entered` and Python log-level names (`critical` appears in a shipped test INI); both are still accepted so old INIs keep working.

## `validate(cfg)`
Runs at the top of `_run`, before any raster is read, and reports every problem in one message:
- input files the run will actually use that do not exist, or are still an INI Builder `(Browse for …)` placeholder — only the files the scenario needs are checked (advanced needs sources/grounds, not a point file; `polygon_file` only if `use_polygons`, etc.)
- an output directory that does not exist (`write_config` used to fail on it with a bare `SystemError`)
- `low_memory_mode` / `preemptive_memory_release` set to `True` — parsed for INI compatibility but never implemented (0 reads outside `config.jl`), so a user relying on them for a large grid (#232, #292, #415) now finds out up front

The docs table for those two options and for `log_level` is updated to match.

## Not in this PR
`use_reclass_table` and `set_focal_node_currents_to_zero` were also unimplemented; they are implemented in #482 and the reclass PR rather than rejected here.

**Tests**: 21 new assertions in `test/internal.jl` covering each rejected value, placeholder detection, that only in-use files are checked, advanced-mode file requirements, the not-implemented options, and that unknown keys are tolerated. Full suite passes locally (Unit 38/38, CG+AMG 719, CHOLMOD 719, Issue 341 46).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a98db13073a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.