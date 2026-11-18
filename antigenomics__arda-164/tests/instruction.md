# Issue

**Title:** Release ARDA 2.38.6: preserve local junction translation across upstream phase shifts

## Description

Correct local junction translation when upstream V indels shift the whole-receptor coding phase. The bridge now follows the observed junction anchor span; observed nucleotide sequence, coordinates and global VJ phase are preserved. Derived stop/productivity labels can change when the corrected local translation exposes an invalid junction; canonical local amino acids do not establish whole-receptor productivity.

Adds neutral regressions for upstream phase offsets, genuine local frameshifts and native upstream V indels. Search, scoring, scientific defaults and dependency requirements are unchanged. Synchronizes package and Nextflow versions to 2.38.6.

Validation: 1,518 local tests passed with 10 optional skips before the metadata-only release bump; 34 focused/native/version checks pass on the release candidate, Ruff and warnings-as-errors Sphinx build pass. Independent source/release review found no blockers. CI must pass before merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c31533f5162`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.