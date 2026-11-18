# Issue

**Title:** refactor: replace EhrapyConfig with scverse-misc Settings

## Description

## Summary

- Replaces the hand-rolled `EhrapyConfig` class (361 lines of properties, setters, and `_type_check` boilerplate) with a `scverse_misc.Settings` subclass (75 lines of declarative pydantic fields).
- Adds `scverse-misc[settings]>=0.0.7` as a dependency.
- .

### User-visible changes

- `ep.settings` is now a `scverse_misc.Settings` instance. Assignment is validated by pydantic, so `ep.settings.verbosity = "nope"` raises `ValidationError` instead of silently storing a bad value, and `ep.settings.verbosity = 4` now needs to be the string `"hint"` (the int form is gone).
- Local overrides via `with ep.settings.override(n_jobs=8): ...` (provided by scverse-misc).
- Settings can be loaded from environment variables (`EHRAPY_N_JOBS=8`) and `.env` files.
- `ep.settings.set_figure_params(...)` is removed; users should call scanpy's `sc.set_figure_params` or set matplotlib `rcParams` directly.
- Dead internal state (`_start`, `_previous_time`, `_previous_memory_usage`, `_low_resolution_warning`) is dropped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `749c0ac73a21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.