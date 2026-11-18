# Issue

**Title:** Add the MIT license file of the Python API client

## Description

The `metagraph-api` client declares MIT in `setup.py`, and its `MANIFEST.in` includes `LICENSE`, but there was no license file in `metagraph/api/python`. So the sdist shipped without a license text, and the repository's top-level GPLv3 `LICENSE` made the client's license unclear.

This adds the MIT text, in the same form as `metagraph/workflows/LICENSE`. The CLI and pymetagraph stay GPLv3.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Adds the missing MIT license text to `metagraph/api/python` so the `metagraph-api` client ships with the license it already declares in `setup.py` and `MANIFEST.in`.

Previously the sdist shipped without a license file, and the repository's top-level GPLv3 `LICENSE` made the client's license unclear. The added text matches `metagraph/workflows/LICENSE`; the CLI and pymetagraph stay GPLv3.

<sup>Written for commit 47d03b37cf5830c9e2917bb56534bf8fe54935ec. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/701?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/701?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F701&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b801d6f4972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.