# Issue

**Title:** Fix Google Benchmark 1.5.5 builds with recent Clang

## Description

Disable thread-safety analysis in optimized builds of the vendored benchmark dependency, whose older annotations fail with recent Clang. Keep BioDynaMo compiler flags unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3be850bbaa25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.