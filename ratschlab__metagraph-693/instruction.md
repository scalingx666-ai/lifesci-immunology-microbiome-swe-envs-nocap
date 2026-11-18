# Issue

**Title:** Reject --align-chain up front where seed chaining cannot work

## Description

## Problem

`metagraph align --align-chain` printed nothing for any read whenever seed chaining could not run.

Seed chaining needs seed coordinates. The labeled aligner has them only with an annotation with coordinates, and only on a BASIC-mode graph: `AnnotationBuffer` disables coordinates on CANONICAL and PRIMARY graphs. In every other case, `align_both_directions`:
- logged "Chaining only supported for seeds with coordinates. **Skipping** seed chaining.";
- then called `exit(1)` from a worker thread.

So the run aborted with no output, and the message claimed the opposite of what happened. The broken cases:
- no annotation;
- an annotation without coordinates;
- any CANONICAL or PRIMARY graph.

## Fix

- `align_to_graph` checks the requirements right after loading the graph and annotation. If they aren't met, it fails with: `--align-chain requires a BASIC-mode graph and an annotation with coordinates (e.g., annotate --coordinates, then transform_anno --anno-type column_coord)`.
- The message in the aligner no longer claims to skip chaining.
- Making chaining work on CANONICAL graphs would need coordinate support in `AnnotationBuffer` for those modes. That is out of scope.

## Test

Integration test `TestDNAAlign.test_align_chain_requires_coordinates`:

| graph | annotation | expected |
|---|---|---|
| BASIC | plain column | rejected, with the message, no stdout |
| CANONICAL | `column_coord` | rejected |
| BASIC | `column_coord` | accepted; one line per read |

It passes locally (filtered run only).

## Before / after

Setup: 24-genome k=31 graph, 30 ONT reads.

| case | master `8b77fc8f9` | this PR |
|---|---|---|
| BASIC, plain annotation | exit 1 after loading; 0 lines; "Skipping seed chaining" | exit 1 in 0.12 s; clear requirement message |
| CANONICAL, plain annotation | exit 1; 0 lines; same misleading message | exit 1 in 0.15 s; clear requirement message |
| BASIC, `column_coord` annotation | exit 0; 30 lines | exit 0; 30 lines (unchanged) |

No effect on normal alignment. `metagraph align -p 8`, CANONICAL, 945 long reads, 3 interleaved repeats each, median wall, master → this PR:
- labeled seed 19: 47.4 → 46.5 s;
- labeled full k: 28.3 → 25.7 s;
- unlabeled seed 19: 42.0 → 38.8 s.

Spreads overlap on all three; peak RSS is the same; output checksums are identical in all 18 runs.

Related observation, not addressed here: on BASIC graphs with a coordinate annotation, labeled alignment of reads with indels mostly fails, with or without `--align-chain`. ONT 400 bp at 3% error: 23/100 aligned, vs. 97/100 with the plain column annotation. Illumina-like reads with substitutions only are unaffected (95/100 either way). The coordinate-consistency check in `LabeledExtender` probably requires exact coordinate distances, so indels break it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes `metagraph align --align-chain` so unsupported configurations fail up front with a clear message instead of printing no reads and aborting with a misleading error.

Seed chaining needs seed coordinates, and the labeled aligner only has them with a coordinate annotation on a BASIC-mode graph. CANONICAL and PRIMARY graphs disable coordinates, so `--align-chain` previously logged "Skipping seed chaining" and then exited from a worker thread. `align_to_graph` now validates the graph mode and annotation type right after loading and returns `--align-chain requires a BASIC-mode graph and an annotation with coordinates (...)`. The message in the aligner no longer claims it is skipping chaining. Adds an integration test covering the rejected and accepted cases.

<sup>Written for commit 29083dbd8b9d0da026d01ac32290c092d0fb8f70. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/693?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/693?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F693&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b77fc8f9e16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.