# Issue

**Title:** feat: rename `--skip_adapter_trimming` and `--skip_deepmased`

## Description

Resolves the two parameter-naming TODOs left in `main.nf` by the typed-parameters conversion (#1103).

### `--skip_adapter_trimming` → `--skip_longread_adapter_trimming`

The old name was ambiguous, since it only ever applied to long reads. Because it exists in released versions, this is a real deprecation: the old parameter is kept (hidden in the schema, marked `[DEPRECATED]`), still works everywhere via `params.skip_longread_adapter_trimming || params.skip_adapter_trimming`, and emits a warning like the other deprecated parameters (`--gtdbtk_skip_aniscreen`, `--skip_metaeuk`).

### `--skip_deepmased` → `--run_deepmased`

Here no deprecation is needed: DeepMAsED was added in #1051 and only exists on `dev`, never in a release, so no user can have `--skip_deepmased` in a working command. `skip_deepmased` also defaulted to `true`, which is a double negative for an opt-in tool. Renaming to `run_deepmased` (default `false`) preserves the exact same behaviour and matches the `--run_*` convention used by `--run_pypolca`, `--run_busco`, etc.

Also updated: schema, `conf/test_minimal.config`, `conf/test_assembly_input.config`, docs and changelog.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de969dc86024`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.