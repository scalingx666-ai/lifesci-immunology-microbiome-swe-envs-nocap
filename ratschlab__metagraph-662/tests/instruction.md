# Issue

**Title:** Own BOSS storage safely across failed loads

## Description

`BOSS::load` could access freed storage for an unknown representation tag, or leave dangling pointers when allocating replacement storage failed.

Own the two buffers with `unique_ptr` and reject unknown tags. Keep the existing free-before-allocate points to avoid retaining large old buffers during replacement. Add a regression test covering failed loads followed by a valid retry.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes memory safety in `BOSS::load` so failed loads can't leave dangling pointers or access freed storage.

- Owns the W and last buffers with `unique_ptr` and rejects unknown representation tags instead of dereferencing them.
- Keeps the free-before-allocate points so large old buffers aren't retained during replacement.
- Adds a regression test covering failed loads from unknown tags and truncated payloads, followed by a valid retry.

<sup>Written for commit d15bd55d996c7f4ae10ff538ab97b2d544efdf25. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/662?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/662?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F662&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ee9a40d510e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.