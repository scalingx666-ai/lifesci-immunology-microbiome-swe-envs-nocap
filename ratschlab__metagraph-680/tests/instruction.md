# Issue

**Title:** Fix SIGSEGV in labeled alignment on CANONICAL graphs

## Description

## Problem
`metagraph align -a <anno>` crashes with SIGSEGV in `LabeledExtender::flush()` on CANONICAL-mode graphs. A read only needs a mismatch or indel near its start. Minimal case: a 48-bp reference, a 47-bp query whose first base mismatches, and k=31. Debug builds trip the assert in `LabeledExtender::set_seed` ("all seed nodes have labels").

## Root cause
When the forward extension has a left clip, `align_both_directions` reverse-complements it and uses the result as the seed of the backward pass. On a CANONICAL graph, `rc_graph == graph_`, so those seed nodes are the opposite-strand node indices. They were never queued in the `AnnotationBuffer`. `set_seed` assumes they already have labels. `flush()` then dereferences the null label set returned by `get_labels()`.

BASIC graphs (rc via `RCDBG`) and PRIMARY graphs (wrapped in `CanonicalDBG`, which maps to base nodes) are not affected.

## Fix
In `LabeledExtender::set_seed`, if any seed node has no labels yet, queue the seed path and fetch its annotations. Otherwise behavior is unchanged.

## Tests
- New `LabeledAlignerTest.CanonicalBackwardExtensionMismatch` covers CANONICAL and PRIMARY on all 7 graph/annotation types. It aborts on master and passes with the fix.
- Local Debug run: `unit_tests_parallel.sh -j 8` filtered to the alignment tests (all `DBGAligner*` and `LabeledAligner*`) passed 207/207. The full suite is left to CI.
- `metagraph align -a` on 350 reads simulated from `tests/data/transcripts_1000.fa` (k=31, canonical): no crash. The output is identical with `-p 1` and `-p 8`.

`query --align` and the server's align endpoint use the unlabeled `DBGAligner` and never reach this code. `LabeledAligner` is only constructed in `cli/align.cpp`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes the SIGSEGV crash in `metagraph align -a` on CANONICAL-mode graphs when a read has a mismatch or indel near its start.

On CANONICAL graphs, backward extension seeds are reverse complements of forward extensions, so their nodes were never queued in the `AnnotationBuffer`. `LabeledExtender::set_seed` now fetches labels for seed nodes that lack them.

- Adds a regression test covering CANONICAL and PRIMARY modes across all graph and annotation types.

<sup>Written for commit 0d5206ee1efd29be8c7321c34fbf414ad798a460. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/680?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/680?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F680&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7f51b0f125a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.