# Issue

**Title:** Expose batched alignment candidates in ARDA 2.38.0

## Description

Add `arda.alignment_candidates` so probabilistic consumers can retain alternative V/J targets and allele groups, scored per-allele D evidence, mismatches, CIGARs and query/reference coordinates before best-hit reduction. Candidate spans remain preliminary evidence; ordinary AIRR annotation keeps its existing behavior.

The API bounds input batches, exposes search limits, validates coordinates, and uses the selected CPU budget sequentially for MMseqs and a deterministic native D batch. Prepare version 2.38.0 and update the required Nextflow pins.

Validation: 1,414 unit/synthetic/real-world tests passed (9 optional OLGA tests skipped); 41 affected candidate/thread/integration checks passed after final adjustments; source lint and strict documentation build passed. Live MMseqs integration retained multiple targets, and native D output matched across thread counts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8cca978e85c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.