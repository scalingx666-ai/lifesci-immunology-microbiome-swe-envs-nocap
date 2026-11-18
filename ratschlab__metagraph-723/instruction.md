# Issue

**Title:** Share read-only annotation storage and fix dense mmap merges

## Description

Dense annotation merges with `--mmap` can write into read-only storage and crash. Use SDSL-owned packed views backed by shared read-only mappings, and convert explicitly to owned storage before mutation. Reuse uniquely owned allocations where possible.

Keep legacy annotation-header parsing in MetaGraph. Update the SDSL dependency for generic rank/select support and the fork's loader bridge, retaining its exact-bit-size copy and sparse-lookup fixes. Cache the dense OR word count before the loop to avoid repeated division. The annotation file format is unchanged.

Retained UHGG and GnomAD merge results matched their references. Compared with the previous revision `306d0c11`, GnomAD chrY + chr21 merge and final compression changed from 200.6 to 202.6 seconds, with about 9.96 GiB peak memory in both versions. These are two repetitions on selected inputs, excluding output-file writing; the timing ranges overlap. Repeated local dense merges were level with that revision.

The shared-view change preserves existing annotation formats. The SDSL upgrade requires rebuilding large HYB vectors that use certain custom superblock rates; MetaGraph's default rate of 16 is unaffected. See the [SDSL compatibility note](https://github.com/ratschlab/sdsl-lite/blob/47e4ebd8eeb24f6e3de399db06ae1934037ed59f/README.md) for the affected rates and size thresholds.

Prepared with Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33ad588d2f41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.