# Issue

**Title:** Build with GCC 14, 15 and 16 in CI

## Description

CI now also builds with GCC 14, 15 and 16. Each new compiler gets one job (DNA, Release, dynamic, AVX). GCC 13 keeps the full matrix and stays the compiler for release binaries.

Ubuntu 24.04 ships GCC 14. GCC 15 and 16 come from the `ppa:ubuntu-toolchain-r/test` PPA, which the install step adds only when apt has no package for the requested compiler. The PPA's GCC 16 is a snapshot from 2026-03-15.

With `-Werror`, GCC 15 and 16 stopped on three warnings. Two are in vendored code, so this PR updates both submodules:

- sdsl-lite: `select_support_rrr` declared a copy assignment that did what the default does. This made its implicit copy constructor deprecated (`-Wdeprecated-copy`), so copying a wavelet tree over `rrr_vector` failed. The assignment is removed.
- DYNAMIC: `#pragma omp master` is deprecated since OpenMP 5.1 (`-Wdeprecated-openmp` in GCC 16). It is replaced with `#pragma omp single`, which works with every OpenMP version. The region only spawns tasks and waits for them, so the result is the same.

The third is a GCC 16 `-Warray-bounds` false positive in `test_bitmap.cpp`. GCC guessed the target of a virtual call through a `bitmap_dyn` pointer and warned about the inlined guess. The test now checks `bitmap_vector` and `bitmap_adaptive` through a template, which avoids the warning and the runtime flag.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/748?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/748?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F748&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13e17ada8141`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.