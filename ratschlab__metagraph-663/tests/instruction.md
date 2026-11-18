# Issue

**Title:** Update SDSL fork with hybrid query cleanups

## Description

Update the SDSL fork pin with hybrid-query simplifications from : bounded spans, simpler minority-position queries, and boolean bit flags with XOR for access results. Also pick up the fork's modern attribute declarations.

The update changes no stored fields or serialization layout. All 379 local vector, wavelet and BOSS tests pass; 250 before/after serialization fixtures match byte for byte.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Updates the SDSL fork pin with hybrid-query simplifications from : bounded spans, simpler minority-position queries, and boolean bit flags with XOR for access results, along with the fork's modern attribute declarations.

No stored fields or serialization layout changes. All 379 local vector, wavelet, and BOSS tests pass, and all 250 serialization fixtures match byte for byte.

<sup>Written for commit 5dd13f43bf129c9235700fa27b1cba2a1a12570e. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/663?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/663?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F663&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `beda064f93d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.