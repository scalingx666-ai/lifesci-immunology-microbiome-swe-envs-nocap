# Issue

**Title:** Select installed OpenSSL 3 in macOS CI

## Description

The macOS build selected preinstalled OpenSSL 4 even though CI installs `openssl@3`. Tests then ran on an older runner image without `libssl.4.dylib` and aborted before starting.

Export the installed `openssl@3` prefix as `OPENSSL_ROOT_DIR` in the shared dependency step, so CMake links the OpenSSL version also installed by the test jobs.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
The macOS CI build selected the preinstalled OpenSSL 4 instead of the `openssl@3` installed by jobs, so tests ran on a runner image without `libssl.4.dylib` and aborted before starting. The shared dependency step now exports the `openssl@3` prefix as `OPENSSL_ROOT_DIR`, so CMake links the same OpenSSL version the test jobs install.

<sup>Written for commit 9ef829f14e2e5df94c560413b8c38b21071df3fa. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/667?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/667?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F667&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36c82ede752e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.