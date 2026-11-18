# Issue

**Title:** Express borrowed k-mer and alignment buffers with spans

## Description

Use `std::span` where code borrows a contiguous buffer:

- Give the k-mer extractor's stored lookup table its actual fixed extent of 128 entries.
- Replace Bloom-filter batch pointer pairs with spans, and bound SIMD loops by the remaining element count.
- Pass the tail of an alignment seed directly to `expand`, removing a temporary vector allocation and copy.

The extractor still borrows its table, and the batch/seed functions consume their inputs synchronously. Consumers must rebuild and update raw pointer-pair calls; stored index formats are unchanged.

Validation: 41 Bloom/k-mer tests, including empty and short batches; seed expansion/lifetime probes and affected translation-unit compilation. The extractor's size is unchanged, its optimized encode functions are byte-identical, and Bloom batch functions retain their vector instructions with three fewer total instructions each (GCC).

Depends on #649 for C++20.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Expresses borrowed contiguous buffers as `std::span` across Bloom filters, k-mer extraction, and seed expansion. This removes raw pointer-pair arguments and a temporary vector allocation when expanding a seed from the tail of another seed, and moves `Seed::expand` out of the header to avoid a GCC 13 warning.

- Bloom-filter batch insert and check now take `std::span<const uint64_t>` instead of pointer pairs, with SIMD loops bounded by the remaining element count.
- The k-mer extractor's lookup table is stored as a fixed-size `std::span<const uint8_t, 128>`, preserving the borrowed lifetime contract with the actual extent.
- `Seed::expand` now accepts a span, so the aligner can pass a slice of the current seed's nodes directly; its definition lives in the `.cpp` file.
- Pulls in SDSL C++20 integration and dependency configuration cleanup from the parent branch.
- Adds tests covering SIMD boundary cases, empty views, borrowed table mutation, and seed expansion from a borrowed tail.

Consumers must update raw pointer-pair calls to pass spans; stored index formats and extractor size are unchanged.

<sup>Written for commit 386fb3a5fec51faede8e7bd51a4eb0bc94fb346e. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/654?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/654?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F654&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06d3bfc15e26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.