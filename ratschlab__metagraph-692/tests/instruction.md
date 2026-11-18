# Issue

**Title:** Add a mapping-only mode to the labeled aligner

## Description

Stacked on #690. Review only the top commit, "Add a mapping-only mode to the labeled aligner"; this PR will be retargeted to master after #690 merges.

## What

`LabeledAligner::map_batch`:
- finds and label-filters seeds exactly as alignment does (`build_seeders` / `filter_seeds`, including `min_exact_match`), but does not extend them;
- reports, per query, the labels whose seeds cover the most query characters on the better strand, plus the number of covered characters and the query range they span (on the forward query).

This supports read accept/reject decisions (e.g. adaptive sampling) that need the label, not a base-level alignment.

The CLI option `metagraph align --align-map-only` is opt-in and off by default. It requires `-a` and supports TSV output only, one line per query:

```
header  strand  labels  covered_chars  query_begin  query_end      (unmapped: header * * 0 * *)
```

Nothing changes in the default `align` path.

## Test

`LabeledAlignerTest.MapWithoutExtension`, typed over all 7 graph/annotation pairs, covers:
- full coverage by one label;
- a query split between two labels, where the larger coverage wins;
- an unmapped query.

7/7 pass locally (assertion-enabled build, filtered run only).

## Numbers (benchmark harness `bench/align-harness`, mode `map`; 24 bacterial genomes, k = 31, CANONICAL, labeled, seed 19)

Single-threaded, per read, alignment vs. `map_batch` on the same reads. The aligned and negative-accepted fractions are identical by construction (same seed filter).

| reads | top-1 label correct (align / map) | p50 ms (align / map) | p99 ms (align / map) |
|---|---|---|---|
| Illumina-like 150 bp | .922 / .921 | 3.0 / 1.9 | 5.8 / 2.7 |
| ONT 400 bp, 3% | .952 / .945 | 8.0 / 3.5 | 20.0 / 5.5 |
| ONT 400 bp, 5% | .679 / .675 | 6.0 / 2.6 | 17.4 / 4.7 |
| ONT 1–5 kb, 3% | .993 / .993 | 69.2 / 27.8 | 295 / 54.5 |
| ONT 1–5 kb, 5% | .827 / .830 | 55.5 / 21.3 | 563 / 47.4 |
| ONT 1–5 kb, 10%, `min_exact_match` 0 | 1.000 / .997 | 66.2 / 13.3 | 397 / 29.5 |
| ONT 400 bp, 10%, `min_exact_match` 0 | .967 / .935 | 6.7 / 1.5 | 21.3 / 2.8 |

Multi-threaded CLI, `-p 8`, 945 long reads (median wall, peak RSS):

| run | wall | peak RSS |
|---|---|---|
| `align`, seed 19 | 45.2 s | 0.95 GB |
| `align --align-map-only`, seed 19 | 14.4 s | 0.67 GB |

No regression in `align`, this PR vs its base, interleaved repeats; output checksums are identical in all three configurations:

| config | base | this PR |
|---|---|---|
| labeled, seed 19 (6 repeats) | 45.2 s | 46.0 s |
| labeled, full k | 26.7 s | 27.8 s |
| unlabeled, seed 19 | 38.0 s | 39.6 s |

The seed-19 spread is 42–49 s on both sides, plus one 68 s outlier on this PR's first repeat.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Adds a mapping-only mode to the labeled aligner that reports the best-supported label per query without extending seeds into alignments. This supports read accept/reject decisions (e.g., adaptive sampling) that need a label rather than a base-level alignment.

`LabeledAligner::map_batch` finds and label-filters seeds exactly as alignment does — including `min_exact_match` — but does not extend them. For each query it reports the labels whose seeds cover the most query characters on the better strand, the number of covered characters, and the query range they span on the forward query. The new `metagraph align --align-map-only` flag is off by default, requires `-a`, and rejects `--json` output; it emits one TSV line per query (`header`, `strand`, `labels`, `covered_chars`, `query_begin`, `query_end`), with unmapped queries reported as `header * * 0 * *`. The default `align` path is unchanged.

**Tests**

- `LabeledAlignerTest.MapWithoutExtension` covers full coverage by one label, a split query where the larger coverage wins, and an unmapped query, across all graph/annotation pairs.

**Benchmarks**

- On simulated Illumina and ONT reads, `map_batch` cuts per-read p50 latency by ~1.5–5× with top-1 label accuracy within ~1–3 percentage points of alignment.

<sup>Written for commit 2fc28b6643c1a37fa196e13d914dd8482651ead7. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/692?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/692?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F692&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa64328f5d70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.