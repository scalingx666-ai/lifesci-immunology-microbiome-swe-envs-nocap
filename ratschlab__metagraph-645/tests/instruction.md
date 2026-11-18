# Issue

**Title:** Run macOS CI natively and key dependency caches by revision

## Description

Keep macOS CI on native Apple Silicon in Debug and Release, and remove the Intel/Rosetta configurations. Unit and integration tests run in both modes; the two library-integration examples continue to run in Debug.

Use Homebrew directly and include the pinned dependency tree in the submodule-cache key. Allow pull requests targeting `codex/**` as well as `master`, so the stacked follow-ups receive CI.

Validation: all three workflow files parse, reusable-workflow inputs match, and the matrix retains 10 Linux and 2 macOS configurations. The [combined run](https://github.com/ratschlab/metagraph/actions/runs/38138235805) passed its Linux/macOS builds, unit tests, integration tests and examples. This draft's separate CI run is pending.

First prerequisite in the focused split of #644. The follow-ups are drafts stacked on this branch.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Runs macOS CI natively on Apple Silicon in Debug and Release, removing the Intel/Rosetta configurations. Unit and integration tests run in both modes; the two library-integration examples continue to run in Debug.

- Installs macOS dependencies via Homebrew directly and keys the submodule cache by the pinned dependency tree revision, so cache hits only occur for the exact dependency tree.
- Pull requests targeting `codex/**` branches now receive CI alongside `master`, so stacked follow-up PRs are tested.

<sup>Written for commit a595eb0851484dfc09df681c669d6e47679523ff. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/645?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/645?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F645&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1de02cec935b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.