# Issue

**Title:** Use C++20 atomics for packed bit-vector helpers

## Description

Use C++20 std::atomic_ref for packed bit-vector words and 64-bit differential counters. The bit-vector helpers accept std::memory_order directly, so the compiler-order conversion switch is removed. Keep the existing builtin operations for packed 8/16/32-bit counters; all counter call sites already use relaxed ordering, so their unused ordering parameter is removed.

A small load-only wrapper works around libc++ versions that cannot instantiate atomic_ref<const uint64_t>::load. The new header uses a project-prefixed guard. Extend concurrent coverage to both setting and clearing bits.

Validation: GCC, Clang and Clang/libc++ concurrency checks pass, as does UBSan. Before/after instruction lists match for 11 bit operations on each compiler (33 comparisons). Targeted translation units and the committed regression test pass. Full CI will rerun after restacking.

Stacked on #649. Review/merge order: #647 → #648 → #649 → #646 → #644.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Switches the packed bit-vector atomic helpers from compiler builtins and integer memory orders to `std::atomic_ref` with `std::memory_order`, since the implicit conversion between them breaks under C++20. A new `utils::atomic_load` wrapper covers const access, which libc++'s `atomic_ref<const T>` cannot instantiate.

- Callers using the atomic flag now pass `std::memory_order_*`; external callers passing `__ATOMIC_*` constants must switch to the standard enum.
- `atomic_fetch` and `atomic_fetch_and_add` dropped their memory-order parameter and are always relaxed; 64-bit counters use `atomic_ref` while 8/16/32-bit counters keep the builtin operations.
- Adds a concurrent test verifying each bit transitions exactly once across five memory orders, for both setting and clearing.

<sup>Written for commit 40a6222085026eb69791882dc27992580355599a. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/646?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/646?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F646&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcca630c013c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.