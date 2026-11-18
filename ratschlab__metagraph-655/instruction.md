# Issue

**Title:** Use standard string prefix and suffix predicates

## Description

Replace the custom prefix/suffix helpers with C++20 `starts_with` and `ends_with`. This removes the temporary substring allocation in suffix checks and avoids copying filesystem paths just to inspect their suffix. Preserve the existing `make_suffix` behavior, including empty suffixes and names already ending in that suffix.

Validation: existing tests plus empty, embedded-NUL, repeated-suffix and path cases; 132,496 generated string pairs compared with the old implementation under GCC and Clang. The removed `utils::starts_with`/`utils::ends_with` helpers require out-of-tree callers to use the standard string members.

Depends on #649 for C++20.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Replaces the custom `utils::starts_with`/`utils::ends_with` helpers with the C++20 standard `starts_with` and `ends_with` string members. This removes the temporary substring allocation in old suffix checks and avoids copying filesystem paths just to inspect their suffix. `make_suffix` and `remove_suffix` behavior is preserved, including empty suffixes, embedded NULs, repeated suffixes, and names already ending in that suffix. Also brings in updates merged from the C++20 parent branch, including SDSL changes, packed counter lock sharding, and dependency configuration cleanup.

**Migration**
- Out-of-tree callers of the removed `utils::starts_with`/`utils::ends_with` helpers must use the standard string members.

<sup>Written for commit a6fab3298013aff1b5588cadbfe1a83f12ce0321. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/655?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/655?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F655&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06d3bfc15e26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.