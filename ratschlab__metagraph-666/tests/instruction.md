# Issue

**Title:** Update SDSL with hybrid query cleanups

## Description

Update SDSL to the hybrid-query cleanups from : separate access/rank/select helpers, simpler minority counts, and byte-sized internal positions and select offsets. Public query conventions and stored formats are unchanged.

Rebuilt MetaGraph’s core and passed 381 vector, wavelet and BOSS tests. All 250 compatibility fixtures remain byte-identical, with 4.7 million hybrid queries checked after loading old-pin files.

Benchmark results and remaining compiler-specific slowdowns are documented in the upstream PR.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Updates the `sdsl-lite` submodule to the hybrid-query cleanups from : separate access/rank/select helpers, simpler minority counts, and byte-sized internal positions and select offsets. Public query conventions and stored formats are unchanged.

Rebuilt MetaGraph's core and passed 381 vector, wavelet and BOSS tests. All 250 compatibility fixtures remain byte-identical, with 4.7 million hybrid queries checked after loading old-pin files.

Benchmark results and remaining compiler-specific slowdowns are documented in the upstream PR.

<sup>Written for commit 91f9473ebe0b4a7192967ae89d1327d7a8d5a5aa. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/666?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/666?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F666&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36c82ede752e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.