# Issue

**Title:** Install the CUDA wheels of rapids-singlecell in the GPU extras

## Description

The `rapids12` and `rapids13` extras now install `rapids-singlecell-cu12[rapids]` and `rapids-singlecell-cu13[rapids]`. rapids-singlecell 0.18 dropped the old extras and only publishes wheels under these names, so the GPU tests have failed on every main commit while building it from source.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a770588d5e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.