# Issue

**Title:** fix #3515: run register_commands off the ioloop

## Description

## Summary

- . `ReloadPluginAPItestHandler.post()` was calling `register_commands()` synchronously, which shells out via `Popen.communicate()` and blocks the master Tornado ioloop for the duration of the plugin register subprocess.
- The subprocess calls back into qiita through nginx, which round-robins across master and workers — so any callback that lands on master while it is still blocked times out (504), breaking CI for plugins that register more than one command (e.g. `qtp-biom`).
- This change awaits `register_commands()` on the default `IOLoop` executor so master stays responsive to the `/activate/` callbacks while the subprocess runs. `_system_call` and `register_commands` are untouched; all their other callers already run outside an ioloop context.

## Why this shape

- `@authenticate_oauth` is already compatible with `async def` — `APIAnalysisMetadataHandler.get` in `qiita_db/handlers/analysis.py` uses the same pattern.
- `activate()` stays synchronous: it is a fast `TRN` write, not the thing that blocks.
- Only `ReloadPluginAPItestHandler` calls `register_commands()` anywhere in the repo, so the blast radius is this one method.

## Test plan

- [x] `pytest qiita_db/handlers/tests/test_plugin.py::ReloadPluginAPItestHandlerTests -v` passes locally.
- [x] CI green on the `qiita_pet qiita_core qiita_ware` matrix leg, which exercises this handler with a real plugin subprocess.
- [x] Confirm the qtp-biom flake in qiita-spots/qtp-biom#33 no longer reproduces against this branch (with nginx upstream restored — i.e. master un-`down`ned).

Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32e1cde20a6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.