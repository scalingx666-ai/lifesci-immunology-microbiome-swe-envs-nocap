# Issue

**Title:** Split `main.py` into CLI, pipeline and config modules

## Description

`main.py` had grown to ~1000 lines mixing CLI code, pipeline orchestration and helper functions. This PR reorganises it without changing behaviour.

### Changes
- **`main.py`**: CLI only (options, logging setup). Builds a `RunConfig` and calls `pipeline.run()`.
- **`pipeline.py`** (new): the run is split into named stages (parse inputs, annotate contigs, assess input bins, create intermediate bins, select bins, write outputs).
- **`config.py`** (new): `RunConfig` (run parameters) and `OutputPaths` (output file locations) dataclasses.
- Small helpers moved to their modules: `resolve_checkm2_db` / `result_parameters` → `diamond.py`, `log_selected_bin_info` → `bin_quality.py`, `can_reuse_step` → `Checkpoint.can_reuse()`.
- Unit tests moved next to the code they test. API docs now list `checkpoint`, `config` and `pipeline`.

No change to the CLI, outputs or results: the functional tests are unchanged and pass, and `binette -h` is identical.

This refactoring was implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c623caa06338`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.