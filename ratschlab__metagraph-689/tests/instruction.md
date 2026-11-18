# Issue

**Title:** Reset the count after G when parsing a CIGAR string

## Description

`Cigar(std::string_view)` did not clear the pending count after a `G` (node insertion), so `"2G3="` parsed as `2G23=` and `"3=2G1X1G"` as `3=2G21X1G`. Every other operation clears it.

Adds a round-trip test, `DBGAlignerTest.cigar_string_round_trip`. A standalone build of `aligner_cigar.cpp` reproduces the bug before the fix and round-trips all three test strings after it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes CIGAR string parsing so a node insertion (`G`) resets its count, preventing `"2G3="` from parsing as `2G23=` and `"3=2G1X1G"` as `3=2G21X1G`.

Adds a round-trip test verifying three CIGAR strings serialize back to their original form.

<sup>Written for commit 96a36f027dcec509faaeb090109d5fb3f4af63de. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/689?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/689?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F689&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b77fc8f9e16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.