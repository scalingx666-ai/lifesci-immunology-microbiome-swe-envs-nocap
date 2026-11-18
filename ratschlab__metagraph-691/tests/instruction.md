# Issue

**Title:** Label seeds that match only a source dummy k-mer on BASIC graphs

## Description

Stacked on #690. Review only the top commit, "Label seeds that match only a source dummy k-mer on BASIC graphs"; this PR will be retargeted to master after #690 merges.

## Problem

On BASIC graphs, the labeled aligner misses seeds shorter than k that occur only within the first k−1 characters of an input sequence.
- Such a string S is a k-mer suffix only of a source dummy k-mer `$…$T`.
- With the graph unmasked, as `align_to_graph` does and as graphs are built by default, suffix seeding finds that dummy k-mer.
- But dummy k-mers have no annotation, so `filter_seeds` drops the seed.
- CANONICAL graphs recover the hit from the other strand, and PRIMARY graphs (CanonicalDBG) from the existing `suffix_to_prefix` pass.

## Fix

In `AnnotationBuffer::fetch_queued_annotations`, on BASIC succinct graphs:
- For a source dummy k-mer that fetched an empty label set, walk forward through its `$` count to the real k-mers that continue it. They all start with T.
- Give the dummy the union of their labels, with coordinates shifted back to the dummy k-mer's start.
- Seeds on the dummy and extensions through it then get labels like any other node: label and coordinate consistency in `LabeledExtender` work unchanged.
- **Fan-out cap:** a dummy continued by more than 16 real k-mers keeps its empty set, the same drop-the-locus rule as `max_num_seeds_per_locus`. For scale, on a 24-genome graph with 19-mer seeds, the forward-resolution fan-out over read windows has p50 1, p99 3 and p99.9 ≤ 14.
- Real annotated k-mers never fetch an empty set, so the extra check runs only for dummy k-mers.

## Test

`LabeledAlignerTest.SubkSeedLabels` (BASIC, CANONICAL and PRIMARY; A = `TTACGAAA`, B = `ACGTTGCA`, k = 5, seeds ≥ 3):
- It checks `ACGT` → B, `TACGA` → A, `CGTTG` → B and `TGCA` → B, and that every reported label contains the aligned sequence on either strand.
- Without the fix it fails on BASIC for `ACGT`; with it, it passes. Checked locally, assertion-enabled build, filtered run only.

## Before / after (benchmark harness `bench/align-harness`, labeled, seed 19)

Targeted set: the first 20/25/30 bp of each of the 42 contigs of a 24-genome graph, both strands (252 reads).

| graph | aligned, before → after | top-1 label correct, before → after |
|---|---|---|
| BASIC | 0.286 → **0.976** | 0.143 → **0.857** |
| CANONICAL (control) | 0.976 → 0.976 | 0.845 → 0.845 |

BASIC per strand: `+` 36 → 123 of 126, `−` 36 → 123 of 126.

Regression check: simulated reads (150 bp Illumina-like; ONT 400 bp and 1–5 kb at 3/5/10% error) on BASIC and CANONICAL.
- 16/16 arms have byte-identical output apart from latency. Random reads almost never start in a sequence's first k−1 bases.
- p50/p99 latency is unchanged within noise.

Multi-threaded CLI, `metagraph align -p 8`, labeled BASIC graph, 945 long reads, 3 interleaved repeats each (median wall, before → after):

| config | wall | peak RSS |
|---|---|---|
| seed 19 | 19.14 → 18.83 s | 0.71–0.73 GB both |
| full k | 9.12 → 9.28 s (spread 8.84–9.93) | 0.63–0.70 GB both |
| unlabeled, seed 19 | 24.79 → 24.65 s | 0.49–0.55 GB both |

Output checksums are identical in all three configurations.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes the labeled aligner dropping seeds shorter than k that occur only within the first k−1 characters of an input sequence on BASIC graphs. Such seeds match only source dummy k-mers `$…$T`, which carry no annotations and were filtered out; CANONICAL and PRIMARY graphs recovered them through separate passes.

- On BASIC succinct graphs, the annotation buffer now resolves a source dummy k-mer with an empty label set by walking forward to the real k-mers that continue it (all start with T) and assigning their labels, with coordinates shifted to the dummy's start.
- Dummies continued by more than 16 real k-mers keep an empty label set, so the locus is dropped as if it had too many matches.
- Adds `LabeledAlignerTest.SubkSeedLabels`, covering BASIC, CANONICAL, and PRIMARY modes.

<sup>Written for commit be7c376e5d5024a11afe6a2db3808d4ebada1130. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/691?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/691?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F691&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cbfe88979bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.