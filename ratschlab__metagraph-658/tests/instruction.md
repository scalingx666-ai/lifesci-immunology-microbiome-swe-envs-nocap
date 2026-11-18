# Issue

**Title:** Simplify bitmap constructor dispatch

## Description

Bitmap graphs already limit k-mers to 63 bits, so the factory's 128/256-bit branches are unreachable. Replace the helper, aliases and argument macro with one local C++20 factory over the existing storage types.

Add coverage for weighted storage boundaries, saturation and invalid arguments. Construction algorithms and serialized formats are unchanged.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Simplify bitmap constructor dispatch by removing the unreachable 128/256-bit k-mer branches and replacing the templated helper, aliases, and argument macro with a local C++20 factory over the existing storage types. Adds tests covering weighted storage boundaries, saturation, and invalid arguments. Construction algorithms and serialized formats are unchanged.

<sup>Written for commit 1298384bb09fe3ca3204d590c3febfc0248bd990. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/658?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/658?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F658&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e97d24abf9e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.