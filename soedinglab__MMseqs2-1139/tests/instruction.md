# Issue

**Title:** Fix hit identity during long-target ungapped rescoring

## Description

## Summary

Fix incorrect sequence lookup when rescoring long targets in full SIMD diagonal bins. The sorted scoring entry now resolves its originating hit once and uses that hit consistently for sequence lookup and score assignment.

## Issue

`UngappedAlignment::scoreDiagonalAndUpdateHits` sorts full diagonal bins by target length before SIMD scoring. Each sorted entry stores the original hit position in `seqs[].id`, allowing scores to be written back to the correct `CounterResult`.

Targets with 32,768 residues or more receive a temporary length of zero so that SIMD scoring skips them. They sort ahead of short targets and are subsequently handled by the long-target fallback.

The fallback used two different mappings:

- Score assignment correctly selected `hits[seqs[hitIdx].id]`.
- Sequence lookup incorrectly selected `hits[hitIdx]`.

After sorting, those expressions can refer to different hits. The fallback could therefore fetch one target’s sequence and assign its score to another target.

### Observable effects

If the incorrectly fetched sequence was short, the long-target guard failed. The intended long hit retained its zero score and could be excluded by downstream score filtering.

If the incorrectly fetched sequence was also long, its score could be assigned to the wrong hit.

This affects full bins containing long targets when the query is shorter than 32,768 residues. Partial bins and the early long-query scoring path already preserve hit identity.

## Root cause

The loop position identifies an entry in the sorted array, while `seqs[hitIdx].id` identifies its original hit position. The fallback treated these index domains as interchangeable.

## Change

Resolve the originating hit at the beginning of each sorted writeback iteration:

`CounterResult *const hit = hits[seqs[hitIdx].id];`

Use this pointer for:

1. Initial SIMD score assignment.
2. Database sequence lookup through hit->id.
3. Long-target score assignment.

The fallback continues to fetch the sequence again, preserving the existing remapping-buffer behavior.

## Validation

A temporary regression executable exercised the public `UngappedAlignment::align` API and compared batched scores against `scoreSingelSequenceByCounterResult`, applying the existing 255-point saturation.

| Platform/configuration | Compiled scoring branch | Result |
| --- | --- | --- |
| Apple Silicon, GCC 16.2.0 | Four lanes | PASS |
| x86_64, SSE4.1 | Four lanes | PASS |
| x86_64, AVX2 | Eight lanes | PASS |

Coverage included:

- A 32,768-residue target placed last in an eight-hit fixture.
- Two long targets with distinct, positive reference scores below 255.
- Per-hit short-target comparisons using distinct, unsaturated scores.
- Direct lookup and identity-remapped lookup.

Before the fix, both lookup modes reproduced dropped long-target scores. After the fix, all scenarios passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `057db43b0681`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.