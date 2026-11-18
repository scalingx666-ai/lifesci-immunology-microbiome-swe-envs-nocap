# Issue

**Title:** Bound memory while hashing corpus artifacts

## Description

Corpus save, first-download verification and cache validation previously materialized each entire file solely to compute SHA-256. The largest indexed NPZ is 616,348,983 bytes. Reuse one Python-3.10-compatible streaming helper with 1 MiB chunks across all three paths, preserving digests and atomic download behavior.

Validation: the regression fails on the previous whole-file allocation; all 54 signature tests pass. On the existing largest frozen asset, isolated-process peak RSS changes from 638,599,168 to 34,766,848 bytes with identical SHA-256. No model fitting, parameter changes or native-code changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59da88d7cf8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.