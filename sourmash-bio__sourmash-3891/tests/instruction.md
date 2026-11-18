# Issue

**Title:** CI: fix cargo-binstall and pixi warning

## Description

Nightly CI runs broke because of a install error with `cargo-binstall`, fixed it by bumping version in pixi config.

Also fix a warning in pixi (`project` -> `workspace`), and bump the pixi version in CI to latest.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3282e1e8e94b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.