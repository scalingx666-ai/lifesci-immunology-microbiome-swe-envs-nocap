# Issue

**Title:** Use shared views for RRR, SD and stat vectors

## Description

With `--mmap`, RRR and SD vectors still load through the SDSL fork's legacy mapped `int_vector`. This change reads them through the shared read-only views added in #723. The legacy loader can be removed once the remaining vector families follow.

SDSL gains a defaulted storage parameter for `rrr_vector`, `sd_vector` and the `select_support_mcl` samples. MetaGraph uses it for `bit_vector_rrr`, `bit_vector_sd`, `BinRelWT`, the small wavelet tree and the BOSS suffix ranges. Construction reuses the original algorithms. One shared owner keeps the arrays alive, so copies no longer duplicate them. The file format is unchanged, and old and new builds read each other's files.

`bit_vector_stat` now uses its view type as the bit vector type. `bit_vector_sdsl` therefore keeps no separate storage type and no per-type accessors.

Production comparisons on UHGG, GnomAD, MetaSUB, RefSeq and UniParc annotations gave identical results with level load, query and merge times. Each comparison measured one vector family against the preceding revision. Building a tiny vector costs about 0.1 µs more, and a tiny SD vector uses about 290 bytes more memory. An annotate-to-BRWT run with 100,000 labels of 300 k-mers each finished within run-to-run noise.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/724?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/724?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F724&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22682dede649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.