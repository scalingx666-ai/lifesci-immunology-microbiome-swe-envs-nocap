# Issue

**Title:** Release 5.3.1: bounded corpus reads and batched exact distances

## Description

Prepare 5.3.1 with exact cohort distances computed through existing sparse products for four or more samples, while preserving the direct path for three or fewer samples. Floor logarithmic overlap distances at zero so identical repertoires can be hierarchically clustered. Stream corpus checksums, close NumPy archives on success and failures, and validate initialized Polars pools against allocated CPUs before sample maps.

The parallelism audit covers shared thread/sample maps, spawned file and synthetic-pool batches, native scoring/generation/inference/EM, numerical fitting phases, and delegated engines. Shared CPU resolution bounds kernels within outer workers; child import-time numerical pools are serial and restored in the parent; worker failures propagate. No native algorithms or model parameters change in this release.

Validation: 140 focused overlap, signature, mapper and CPU-budget tests pass; strict Sphinx and strict notebook checks pass. Six new identical-sample regression cases fail before the fix and pass afterward, including actual hierarchical clustering. Earlier unchanged native kernels passed cross-host oracle, determinism and bounded-scaling checks. All fix PRs are merged; only this promotion remains open. Publication waits for all current source checks to pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6353405c203`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.