# Issue

**Title:** Fix bin path corruption when a process emits a single file

## Description

## Description

When a `path("dir/*.fa.gz")` output has no `arity` and the glob matches exactly one file, Nextflow emits a bare `Path` instead of a one-element list. `Path` is `Iterable` over its **path segments**, so `findAll`, `toSorted`, `[0]` and friends iterate the directory names instead of the bins. What survives is a relative one-segment path, which resolves against `launchDir` and gives a broken symlink.

This made GTDB-Tk fail with `There are N paths in the batchfile which do not exist` for any group left with a single prokaryotic bin after Tiara. Groups with two or more bins were fine, which is why it went unnoticed.

## Changes

- Added `arity` to the glob bin outputs in `tiara_classify`, `dastool_rename_pre`, `dastool_rename_post` and `metabinner_bins`, so the channel is a list from the start. Optional outputs use `'0..*'`, because `'1..*'` with `optional: true` fails outright when the glob matches nothing.
- Guarded the consumers with the `[bins].flatten()` idiom already used elsewhere in the pipeline, since bins can also come from `modules/nf-core/*`: GTDB-Tk bin filtering (the reported failure) and CheckM v1 bin sorting (same bug, latent because `run_checkm` is off by default).
- Fixed `reads.toSorted { files -> files[0].getName() }` in the co-assembly grouping. With single-end data `files[0]` returned the first path segment, the same for every sample, so the sort key collapsed. Ordering only, no broken paths.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `034af2b60718`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.