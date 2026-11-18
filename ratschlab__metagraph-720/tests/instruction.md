# Issue

**Title:** Use 64-bit keys for SSHash protein graphs at k=12

## Description

Select the smallest SSHash key type using its `max_k`. This removes the generic odd-length rounding that unnecessarily selected 128-bit keys for protein graphs with `k=12`.

Existing SSHash protein graphs with `k=12` and their dependent annotations must be rebuilt. The release note records this change.

Prepared with Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Selects the smallest SSHash key type using its `max_k` instead of rounding the k-mer length to an odd value, so protein graphs with `k=12` now use 64-bit keys instead of 128-bit keys.

Existing SSHash protein graphs with `k=12` and their dependent annotations must be rebuilt; other k-mer lengths keep their current storage width.

<sup>Written for commit a2653f044669ee5fe3f66b145d17c0d8eae1ed75. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/720?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/720?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F720&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a381fde8822f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.