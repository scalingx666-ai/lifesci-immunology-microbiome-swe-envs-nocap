# Issue

**Title:** Skip UpdateStaticness when detect_static_agents is false

## Description

## Summary
- Adds a `SetUp` override to `UpdateStaticnessOp` that reads `detect_static_agents` once per iteration
- Early-returns from `operator()(Agent*)` when static agent detection is disabled, avoiding a virtual call into every agent's `UpdateStaticness` method

## Test plan
- [ ] Existing unit tests pass (`make check`)
- [ ] Verified that simulations with `detect_static_agents = false` (the default) skip per-agent work in this operation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c8d6f3ac51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.