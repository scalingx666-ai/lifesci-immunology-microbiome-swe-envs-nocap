# Issue

**Title:** Map sequences with node_range in annotated_dbg.cpp

## Description

The eight loops in `annotated_dbg.cpp` that map a sequence to nodes now iterate `node_range(sequence)` in place of the `map_to_nodes` callback. The loop bodies are unchanged. This gives `node_range` (#735) its first callers.

Time per k-mer of the range relative to the callbacks on master (mex, k=31, one core, median of 5 rounds, reads and contigs):

| Graph | Range / callbacks |
|---|---|
| DBGSuccinct, CanonicalDBG | 0.99–1.00 |
| DBGHashFast | 0.95–1.00 |
| DBGSSHash canonical | 0.84–0.94 |

This is the mapping step alone. A full query was not timed.

Prepared with AI assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/739?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/739?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F739&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0df8a0a97cc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.