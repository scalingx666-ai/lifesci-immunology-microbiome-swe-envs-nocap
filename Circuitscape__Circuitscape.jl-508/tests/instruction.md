# Issue

**Title:** Export nothing from Circuitscape

## Description

Part of the unreleased 6.0.

`compute` was the package's only meaningful export (plus `accumulate_current_maps`, `calculate_cum_current_map`, `calculate_max_current_map` from `utils.jl`, which nothing uses unqualified). With `start` already unexported (#480), the public surface is a handful of functions that read more clearly fully qualified — `Circuitscape.compute`, `Circuitscape.start`, `Circuitscape.init_config` — so the package now exports nothing.

- `src/run.jl`: `export compute` removed; docstring updated to show `Circuitscape.compute(...)` and `using Circuitscape: compute`.
- `src/utils.jl`: the three-name export block removed.
- Tests: `test_utils.jl`, `internal.jl`, `issue341.jl` add `using Circuitscape: compute`.
- Omniscape is unaffected: it uses `import Circuitscape: compute_omniscape_current` and qualified `Circuitscape.init_config` / `Circuitscape.update!`.

Docs and README are updated in #507 (all examples become `Circuitscape.compute(...)`; migration page gains the bullet).

Full suite green (see summary in PR checks / commit).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6be7e32eb10e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.