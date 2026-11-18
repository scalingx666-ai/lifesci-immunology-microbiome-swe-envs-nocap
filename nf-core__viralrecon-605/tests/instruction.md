# Issue

**Title:** Homogenize nanopore normalized variant filenames

## Description

## What changed

- Harmonize Clair3/BCFTOOLS_NORM output names with the existing ARTIC `.normalised` convention.
- Update the Nanopore/minimap2 nf-test snapshot expectations.
- Update the documented Clair3 output filenames.

## Why

The Nanopore workflow currently uses `.normalised` for ARTIC outputs but `.norm` for the equivalent Clair3-normalized VCF and index. The shared `ext.prefix` is the root cause and controls both output basenames.

.

## User impact

Clair3 normalized VCF outputs change from `*.norm.vcf.gz[.tbi]` to `*.normalised.vcf.gz[.tbi]`. This intentionally aligns the two Nanopore paths; external globs using the old name will need updating.

## Validation

- [x] Snapshot JSON parses successfully.
- [x] Static checks confirm the old Clair3 paths are gone and all 18 expected VCF/TBI paths use `.normalised`.
- [x] `git diff --check` passes.
- [ ] Targeted Nanopore/minimap2 nf-test and pipeline lint (local environment lacks nf-test/Nextflow and a running Docker daemon; CI will provide the runtime check).

## PR checklist

- [x] This description explains the changes and reason.
- [x] Existing tests and snapshot expectations are updated.
- [x] Output documentation is updated.
- [x] CHANGELOG entry uses this PR's assigned number.
- [ ] CI test suite and lint pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1668569b89d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.