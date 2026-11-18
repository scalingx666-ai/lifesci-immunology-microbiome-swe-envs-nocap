# Issue

**Title:** Update DYNAMIC with upstream CMake fixes

## Description

Update DYNAMIC to the fork revision that incorporates upstream’s C++17 and CMake fixes. The fork keeps MetaGraph’s C++20 setting, reuses its existing dependency targets, and leaves standalone tools disabled.

Only DYNAMIC’s CMake configuration changes; all 28 headers are unchanged. Verified with MetaGraph’s actual dependency helper and a compiled C++20 consumer.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Updates the `DYNAMIC` submodule to a fork revision that incorporates upstream’s C++17 and CMake fixes, fixing the build when using newer CMake versions.

The fork preserves MetaGraph’s C++20 setting, reuses the existing dependency targets, and keeps standalone tools disabled. Only the submodule reference changes; all 28 headers are unchanged. The update was verified with MetaGraph’s dependency helper and a compiled C++20 consumer.

<sup>Written for commit d5f961183969061286eb0c666c6b5a1efca67627. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/665?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/665?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F665&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c605bb1e0b7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.