# Issue

**Title:** Recognise .zst-compressed inputs by their inner extension

## Description

`file_format` handles compressed inputs by looking at the extension before the compression suffix. It compared against `"zst"` without the leading dot, so that branch never matched `.zst`. Any `*.zst` file fell through to the default, which is FASTA. As a result, `file.vcf.zst` was read as FASTA instead of VCF, and `file.fq.zst` was classified as FASTA rather than FASTQ.

I added the dot. A bare `file.zst` now has no format, the same as `file.gz` already does. I extended the `get_filetype` tests with `.zst` cases.

cubic found this while reviewing #704.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixed `file_format` so `.zst`-compressed inputs are recognised by their inner extension. The extension check compared against `"zst"` without the leading dot, so every `*.zst` file fell through to the FASTA default — `file.vcf.zst` was read as FASTA and `file.fq.zst` as FASTA instead of FASTQ. A bare `file.zst` now yields no format, matching how `file.gz` behaves. Added test cases for `.zst` files.

<sup>Written for commit 075bc3ad39bd80088e8a7743d922deefdb161442. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/707?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/707?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F707&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56e538effa8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.