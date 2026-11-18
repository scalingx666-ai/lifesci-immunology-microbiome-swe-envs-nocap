# Issue

**Title:** Replace `.toList().sort()` with `toSortedList()` in PIPELINE_INITIALISATION

## Description

The read/assembly ID cross-validation in `PIPELINE_INITIALISATION` called `.sort()` on the value channel returned by `toList()`. `sort` is not a channel operator. It only works because of an undocumented GPars `DataflowVariable` fallback that turns unknown method calls into derived values. Nextflow does not support this, and future versions may remove it, which would break any run with `--assembly_input`.

This replaces `.toList().sort()` with `toSortedList()`, which emits the same sorted list as a value channel. The downstream `.map` already compares `ids1.toSorted() != ids2.toSorted()`, so behavior is unchanged.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nextflow lint`).
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e5f32c0d74c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.