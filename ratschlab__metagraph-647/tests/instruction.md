# Issue

**Title:** Use ordinary SDSL storage for differential counters

## Description

Use ordinary SDSL storage for differential counters. The existing allocator accessed SDSL private layout through a cast; ordinary storage provides the word alignment this code needs and removes the custom allocator.

Validation: C++17 syntax checks and concurrent counter probes covering 14 packed widths pass. Full CI will rerun after restacking.

Based on master. Review/merge order: #647 → #648 → #649 → #646 → #644.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Replaces the custom aligned allocators for differential counter vectors with ordinary SDSL storage, removing a dependency on SDSL's private object layout.

- Removes `aligned_int_vector` and `aligned_bit_vector` from MetaGraph headers; the differential counter caller now allocates a plain `sdsl::int_vector`.
- C++17 checks against the original SDSL revision pass for 14 concurrent counter widths, five bit-update orders, and 384 ordinary vector allocations, checking alignment and zero initialization.

<sup>Written for commit 48faf0de7d15f8bf2cd851929ca219e7fbb12095. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/647?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/647?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F647&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `670c6c7ab696`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.