# Issue

**Title:** Match Circuitscape 4 output files and map post-processing

## Description

Part of the parity review against Circuitscape 4.0.5.

## Summary
- **Log transform and null-to-nodata are applied at write time.** Per-pair maps are accumulated raw and only the written grid is transformed, so with `log_transform_maps` the cumulative map is log10 of the sum rather than the sum of logs, and cells with zero current in one pair are no longer nodata in the cumulative map. New `write_current_grid` / `write_voltage_grid` helpers apply `log_transform_maps`, `set_null_currents_to_nodata` and `set_null_voltages_to_nodata` to every written grid: pairwise, advanced, one-to-all per-focal, cumulative and max. Previously only pairwise per-pair maps honoured them.
- **Per-solve current files** are written only when `write_cur_maps` is set and `write_cum_cur_map_only` is not, in network pairwise and in one-to-all/all-to-one; advanced mode writes its current map under `write_cur_maps` or `write_cum_cur_map_only` (6.x behaviour kept; the map is no longer all zero under the latter). One-to-all still accumulates under `write_cum_cur_map_only` alone, so that map is no longer all zero.
- **Output prefix** comes from `splitext` via `output_prefix(cfg)` instead of splitting the path on the substring `.out`, which sent files to the parent directory when a directory name contained it.
- **One-to-all and all-to-one write `<prefix>_resistances.out`** (two columns), as Python does.
- **The INI copy is written to `<prefix>.ini`** rather than into `output_file`, except when that file is the INI being run, which is never overwritten. `write_config` now writes every option; `write_config(cfg)` keeps its 6.1 meaning and `write_config(cfg, path)` is new. Docs updated.
- **An `output_file` ending in a path separator** is rejected by `validate`.
- **Text-list focal points** on the lower-left corner are rejected with the intended message (bounds check `< 1` on 1-based indices).

Kept as CS5: `write_cum_cur_map_only` alone still writes the cumulative map in every mode, which the docs define as Julia's behaviour; Python writes nothing in that case. The max map keeps its CS5 name `_max_curmap` (CS4: `_curmap_max`).

## Test plan
- [x] New "output files" and "text-list focal node bounds" testsets: prefix helper including a `job.out` directory, exact output file sets per mode, INI sidecar, cumulative equals the sum and max equals the max of per-pair maps, log cumulative equals log10 of the raw sum, nodata only at nodata cells for every grid type, `write_cum_cur_map_only` in all four modes, the one-to-all resistances file, corner point rejection.
- [x] Full `Pkg.test()` passes; no reference outputs changed. The `oneToAllVerify10` per-focal maps are no longer generated (they were compared on master; per-focal coverage remains in the other one-to-all/all-to-one cases).

## Review
See the review comment for the per-item CS4-vs-CS5 determination and follow-up commit 54ce8dc.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c43300d145e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.