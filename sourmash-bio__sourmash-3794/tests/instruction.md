# Issue

**Title:** build: fix pixi task for wasm-pack

## Description

CI for building the NPM wasm package broke after #3561

Solution is to activate env vars per feature (in this case `wasm`), on top of the `default` environment activation that was already set up.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `306573033286`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.