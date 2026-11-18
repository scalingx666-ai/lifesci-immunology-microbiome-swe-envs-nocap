# Issue

**Title:** Add node_range: map a sequence to nodes as a range

## Description

`SequenceGraph::node_range(sequence)` returns an input range over the nodes of a sequence's k-mers, so a caller can write `for (node_index node : graph.node_range(seq))`. `node_range(seq, true)` yields the nodes of `map_to_nodes_sequentially`. The callback interface stays.

Each graph provides a `NodeStream` that fills chunks of nodes. DBGSuccinct, DBGSSHash and DBGHashFast stream directly, and their two callback methods now run on that stream, so each has one mapping loop. `BOSS::map_to_edges` runs on the new `BOSS::EdgeStream`. All other graphs use a default that buffers the callback output.

Behaviour change: `BOSS::map_to_edges` now passes npos to the callback for a k-mer that `skip` rejects. Its three callers are adjusted.

Time per k-mer relative to master's callbacks (mex, k=31, one core, median of 5 rounds, reads and contigs):

| Graph | Range | Callbacks |
|---|---|---|
| DBGSuccinct, CanonicalDBG | 0.99–1.02 | 0.98–1.02 |
| DBGHashFast | 0.84–0.89 | 0.90–0.93 |
| DBGSSHash canonical | 0.59–0.77 | 0.67–0.82 |

The mapping loops in `annotated_dbg.cpp` can move to the range in a follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/735?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/735?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F735&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8ca5aa16b35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.