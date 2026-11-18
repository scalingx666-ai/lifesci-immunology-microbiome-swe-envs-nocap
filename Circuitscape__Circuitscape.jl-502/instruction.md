# Issue

**Title:** Make CSConfig the single configuration past parsing; remove the flags layer

## Description

Part of the unreleased 6.0; the internal changes below are breaking for code that reached into `RasterFlags` / `NetworkFlags` / `OutputFlags`, which is acceptable for 6.0. The public entry points are unchanged.

## The problem

Configuration had two representations past parsing. `CSConfig` was built from the INI / Dict, and then every entry point rebuilt a second copy from it: `get_raster_flags(cfg)` and `get_network_flags(cfg)` produced `RasterFlags` / `NetworkFlags`, `get_output_flags(cfg)` produced `OutputFlags`, and both `flags` and `cfg` were threaded through `solve`, `postprocess`, `write_cur_maps`, `write_volt_maps`, `advanced_kernel`, `onetoall_kernel`, the graph builders and `_get_sources_and_grounds`. Every field on the flags structs was already a field on `CSConfig`.

That duplication is the mechanism behind the parsed-but-never-read class of bugs (#342, #231, `low_memory_mode`): an option can be parsed correctly into `CSConfig` and simply never be copied into the struct the kernels actually consult. Nothing fails; the option is silently ignored. Each fix for one of those bugs had to add a field to `OutputFlags`, populate it in `get_output_flags`, and only then read it.

## The change

* `CSConfig` is built once in `compute` and is the only configuration value passed down. Functions that took `(..., flags, cfg, ...)` now take `(..., cfg, ...)`; argument order is otherwise unchanged.
* `RasterFlags`, `NetworkFlags`, `OutputFlags`, `get_raster_flags`, `get_network_flags` and `get_output_flags` are deleted.
* Every `flags.x` / `flags.outputflags.x` read is the `cfg` field of the same name, or one of the new predicates in `config.jl`: `is_raster`, `is_network`, `is_pairwise`, `is_advanced`, `is_onetoall`, `is_alltoone`, `policy(cfg)` (= `_remove_policy_symbol(cfg.remove_src_or_gnd)`).
* `flags.is_advanced` was also used to tell whether `write_cur_maps` / `write_volt_maps` received an `Output` (pairwise) or a raw voltage vector (advanced). That is now dispatch on the argument type (`_voltages(::Output)` / `_voltages(::AbstractVector)`).
* `write_cum_maps` takes `cfg` instead of two booleans copied out of it.
* `CSConfig(cfg::CSConfig; field = value, ...)` returns a copy with selected fields replaced. `compute_omniscape_current` (used by Omniscape) keeps its `Dict{String,String}` signature and uses it to build a `CSConfig` carrying the same overrides its hand-written `RasterFlags` / `OutputFlags` did (raster, advanced, `rmvsrc`, no maps written, `connect_using_avg_resistances = false`).

With one representation, an option that reaches `CSConfig` is by construction the value the kernels read; there is no second struct to forget to populate. Adding an option is now: add the field, parse it, read it.

Commits are split for review: the first adds the predicates and copy constructor with tests; the second is the mechanical removal of the flags layer.

## What stays compatible

* `compute(path)`, `compute(dict)`, `init_config()`, `parse_config`, `write_config(::CSConfig)` and `write_config(::Dict)` are unchanged. `Dict{String,String}` remains the INI / INI-builder interchange format only: `init_config` defaults, `parse_config`'s intermediate, and `Dict(cfg)` for round-tripping.
* `compute_omniscape_current(conductance, source, ground, cs_cfg::Dict{String,String})` keeps its signature and semantics.
* No behaviour change in any output: the gold-file suite is the check.

## Tests

`JULIA_NUM_THREADS=4 julia --project=. -e 'using Pkg; Pkg.test()'` after rebasing on master (ArchGDAL not installed locally, so the GeoTIFF fixtures are skipped: 685 rather than 719):

```
Unit tests                 |  511    511
CG+AMG, parallel, Float64  |  685    685
CG+AMG, parallel, Float32  |  685    685
CHOLMOD, parallel, Float64 |  685    685
CHOLMOD, parallel, Float32 |  685    685
Issue 341: included pairs  |   46     46
```

`test/internal.jl` gains checks for the predicates and the copy-with constructor; no existing test constructed the flags structs directly, so none needed rewriting.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62187e8845e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.