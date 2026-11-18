# Issue

**Title:** Choose the SSHash minimizer length from the input size

## Description

`build --graph sshash` without `--num-chars` used m = k/2 (15 for k = 31). For large inputs that is well below ceil(log_4(num_chars)) + 1, and SSHash warns about it on every such build. The skew index then dominates both size and build time.

This counts the input characters in a single pass before the build when `--num-chars` is 0, and applies the existing formula. An explicit `--num-chars` still overrides. The chosen m is logged at info level, and the counting time at trace.

On a 4.6 G k-mer slice of a Logan contig set (48 threads, EPYC), `--num-chars` (m = 19) versus the old default (m = 15) gave:
- construction: 1,302 → 761 s
- peak RSS: 40.5 → 27.6 GB
- graph: 9.11 → 6.92 GB

Validation of this branch's binary on the same input (counting cost, query equivalence) will follow in a comment.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Chooses the SSHash minimizer length from the input size when `--num-chars` is not given, instead of using the fixed k/2 default that inflated the skew index for large inputs. The input characters are counted in a single pass before the build, decompressing only `.gz` names the way SSHash reads them, and the chosen `m` is logged at info level. An explicit `--num-chars` still overrides the count.

On a 4.6 G k-mer slice of a Logan contig set (48 threads, EPYC), the new default `m = 19` cut construction from 1,302 to 761 s, peak RSS from 40.5 to 27.6 GB, and graph size from 9.11 to 6.92 GB.

- Tests build inputs on both sides of the m = 7/9 step so a miscount fails.

<sup>Written for commit 1396413a6b37d75ceefb7450456dc46a98b1b016. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/700?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/700?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F700&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b801d6f4972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.