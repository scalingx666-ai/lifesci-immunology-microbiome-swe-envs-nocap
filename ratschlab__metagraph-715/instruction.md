# Issue

**Title:** Remove the top-level Makefile and build the Docker image with CMake

## Description

Remove the hand-written top-level Makefile. The Docker image builds the DNA, DNA5 and protein executables directly with CMake. Source builds still support running `cmake ..` followed by `make` in the build directory.

Prepared with Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Removes the top-level Makefile and builds the MetaGraph Docker image directly with CMake, running `cmake ..` and `make metagraph` for the DNA, DNA5, and Protein alphabets. Source builds still work with `cmake ..` and `make` in the build directory.

**Migration**
- Developers who used `make build-metagraph env=docker` should build directly with CMake following the source installation instructions instead.

<sup>Written for commit 065c974ed4b86f690baa26010fd0ec0744cba476. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/715?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/715?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F715&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1926f1b23db4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.