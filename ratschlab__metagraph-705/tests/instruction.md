# Issue

**Title:** Keep annotation tasks off the per-file batch callback

## Description

In `annotate_data`, each file gets a `BatchAccumulator` whose callback captures `anno_graph` by reference and spawns `#pragma omp task ... shared(anno_graph)`. GCC lowers that task as `firstprivate(__closure)` and reads `__closure->__anno_graph` inside the task (`-fdump-tree-omplower`). The closure lives in the batcher's `std::function`. The batcher is destroyed at the end of each file, and that is also when its destructor flushes the last batch into a task. Those tasks only finish at the implicit barrier, so they can read a destroyed closure. That is undefined behaviour in the coordinates, plain and k-mer-count paths.

Today it goes unnoticed: the closure is small enough to sit in `std::function`'s inline buffer, so the dead stack slot still holds the right pointer. I reproduced it standalone with the same structure and GCC 15 + ASan. Once the closure is large enough to live on the heap, ASan reports `heap-use-after-free` in the task body every time (3/3 runs). Clang copies the reference itself and is not affected.

With the fix, each callback captures `anno_graph.get()` by value and passes it to the task as `firstprivate`, so the task no longer reads the closure. With that change the same repro is clean under GCC and Clang. The graph outlives the parallel region, so the raw pointer is safe.

I found this while assessing #670, which carried the same fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes a use-after-free in `annotate_data` where OpenMP tasks could read the batch callback's captured `anno_graph` reference after the `BatchAccumulator` destroyed its closure at a file boundary. Each callback now captures the graph's raw pointer by value and passes it to the task as `firstprivate`, so tasks no longer depend on the closure's lifetime; the graph outlives the parallel region, so the pointer is always valid.

<sup>Written for commit c22d4555f2f0827fe1f6bce7de59c021cb46e47e. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/705?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/705?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F705&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d9486975912`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.