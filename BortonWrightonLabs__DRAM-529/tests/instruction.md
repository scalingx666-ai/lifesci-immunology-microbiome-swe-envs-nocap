# Issue

**Title:** Feat/mmseqs gpu support

## Description

Add optional GPU acceleration for MMseqs2 searches through the GPU
profile, including GPU database preparation, validation, and per-database
CPU exclusions.

Integrate CPU and GPU searches with the shared batching workflows,
size-based resource allocation, and executor job arrays. Update pipeline
configuration, schema, documentation, and tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01384626bdba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.