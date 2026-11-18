# Issue

**Title:** Bump version to 6.0.0

## Description

Breaking changes since 5.17.1 warrant a major bump:

- `start` is no longer exported; use `Circuitscape.start()` (#480).
- Configuration values that used to be silently defaulted or ignored are now errors (#483): unrecognised `solver`/`scenario`/`data_type`/`precision`/`log_level`/`remove_src_or_gnd` strings, non-boolean values for boolean options, a missing `scenario`, input files that do not exist, an output directory that does not exist, and `low_memory_mode` / `preemptive_memory_release` set to `True`.

Also new since 5.17.1, for the release notes: `set_focal_node_currents_to_zero` (#482) and `use_reclass_table` (#484) actually work; the include-pairs file is honoured in every mode (#449, #472, #473); `residual_tolerance` INI option and CG retry (#486); single precision runs again (#486, #488).

`Project.toml` is the only place the version appears.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fb63980a34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.