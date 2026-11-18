# Issue

**Title:** Remove deprecated workflow telemetry action

## Description

## Summary

- Remove the optional workflow telemetry action that still declares Node.js 20.
- Leave the remaining book-build workflow unchanged.

## Validation

- YAML parsed successfully with `yaml::read_yaml()`.
- `git diff --check` passed.
- Confirmed no telemetry references remain.
- `actionlint` was not available locally.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4db61b951d54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.