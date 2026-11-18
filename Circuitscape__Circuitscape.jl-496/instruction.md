# Issue

**Title:** Move the INI builder into an extension on the REPL stdlib

## Description

The interactive INI builder (`src/INIBuilder/`) was the only user of `REPL` and `REPL.TerminalMenus`. It moves to `ext/CircuitscapeREPLExt/`, with `REPL` as a weak dependency, and `REPL` leaves `[deps]`.

## `Circuitscape.start()` just works, everywhere
- From the **prompt**: REPL is already loaded, the extension is active, `start()` runs the builder as before.
- From a **script**: the core `start(args...)` calls `load_repl_extension()`, which `Base.require`s the REPL stdlib on demand — that activates the extension, which defines the zero-argument `start()` — and then dispatches to it with `invokelatest`. No `using REPL` needed; the docs and README say nothing about it because there is nothing to say. `start(1)` is a `MethodError`, as before.

## Honest note on the benefit
Measured: **PrettyTables** (a dependency of TimerOutputs, used by Circuitscape and AlgebraicMultigrid) depends on REPL and loads it, so in a plain `julia -e` process REPL is already present and this extension is always active today — the on-demand `require` branch is not reached in the current dependency set, and the load-time saving is nil until that chain changes. What this PR buys now is structural: the builder is no longer core code, `REPL` is no longer a direct dependency, and if TimerOutputs/PrettyTables later drops REPL the saving (~0.08 s measured for REPL alone) appears with no further change.

## Tests
Full suite on master (post-#495): Unit 488/488, CG+AMG and CHOLMOD × Float64/Float32 685/685 each (GeoTIFF fixtures skipped without ArchGDAL), Issue 341 46/46. New test: `load_repl_extension()` returns the active extension, `start()` has its zero-argument method, `start(1)` throws `MethodError`. Verified by hand that a script's `Circuitscape.start()` launches the builder.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff9131e0afc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.