# Issue

**Title:** Generate k-mer encoding constants at compile time

## Description

Generate the 2-bit-to-3-bit lookup table from its encoding rule instead of maintaining 256 literals. Use `std::bit_width` for alphabet widths and `std::integral` for encoded-symbol constructor constraints.

The lookup values and bit widths are preserved. Add comparisons between the specialized and generic cross-width conversions.

Focused DNA and Protein tests pass with GCC and Clang. Existing DNA5 and case-sensitive test failures also reproduce on unchanged master; this PR does not change those cases.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Generates the k-mer encoding constants at compile time instead of maintaining them as literals, with no change to lookup values or bit widths.

- Replaces the 256-entry 2-bit-to-3-bit lookup table and the custom `log2` template with a `constexpr` expansion of the encoding rule and `std::bit_width`.
- Restricts the encoded-symbol constructor to `std::integral` types.
- Keeps the table in a raw array to work around a GCC missed-optimization bug (GCC PR127883).
- Adds tests comparing the specialized and generic cross-width conversions; pre-existing DNA5 and case-sensitive failures also reproduce on unchanged master.

<sup>Written for commit 8e1a5164e34c8d0a6d781629ab8cc2181d6f2d8c. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/660?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/660?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F660&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e97d24abf9e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.