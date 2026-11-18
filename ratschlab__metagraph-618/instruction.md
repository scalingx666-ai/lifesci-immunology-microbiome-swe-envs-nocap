# Issue

**Title:** Support loading RowDisk annotations without mmap

## Description

## Summary
The disk-resident row-diff annotators (`RowDiff<RowDisk>`, `IntRowDiff<IntRowDisk>`, `TupleRowDiff<CoordRowDisk>`) previously forced mmap regardless of `--mmap`. Now they respect the flag, with one exception: `boundary_` is always mmap'd (too large to materialize into RAM) and gets `madvise(MADV_RANDOM)` since access is `select1`-driven.

| Component | `--mmap` on | `--mmap` off |
|---|---|---|
| `set_bits_` (`int_vector_buffer<>`) | disk-resident | disk-resident |
| `boundary_` | mmap | **mmap** |
| `anchor_`, `fork_succ_` | mmap | RAM |

## Mechanism
- `utils::named_ifstream` mirrors `sdsl::mmap_ifstream` (carries the filename); `utils::get_filename(istream&)` recovers it via `dynamic_cast` so loaders work with either stream type.
- `RowDisk`/`IntRowDisk`/`CoordRowDisk` `load()` open a fresh `mmap_ifstream` for `boundary_`.
- `annotation_matrix.cpp` drops the `is_same_v<T, RowDiffDisk*Annotator>` mmap override.

## Test plan
- [x] `RowDiffDiskAnnotatorTest.LoadConsistentAcrossMmapSettings` — round-trip with mmap on/off
- [x] `AnnotatedDBGWithNTest/5.*` (all `RowDiff<RowDisk>` typed tests)
- [x] CI green

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8577374ca0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.