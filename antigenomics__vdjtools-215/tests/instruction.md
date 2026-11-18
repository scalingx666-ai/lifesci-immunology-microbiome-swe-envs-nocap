# Issue

**Title:** Enforce Polars allocation for single-worker sample maps

## Description

A preinitialized four-thread Polars pool was accepted by a one-worker sample map under a two-CPU allocation. Validate the immutable pool against the current allocation when maps start, including the serial path. Reuse the existing pool guard; pooled maps still require serial inner kernels. In-budget wide pools remain valid without an outer pool, and spawned-process maps can leave the parent's unused pool idle.

Validation: 23 focused budget/mapper checks and 154 combined signature/overlap/budget checks pass; strict Sphinx passes. Mirpy cohort/budget integration passes 24 checks with one optional-dependency skip. Regressions cover the original four-thread/two-CPU case, allocation reduction after import, valid preinitialized pools and spawned-process isolation. The branch includes current dev and the 5.3.1 candidate; no model or native-code changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa4793c35ab5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.