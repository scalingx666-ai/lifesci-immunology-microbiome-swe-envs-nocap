# Issue

**Title:** Map CANONICAL SSHash nodes to annotation keys without spelling them

## Description

For a CANONICAL SSHash graph, `AnnotationKeyMapper` spelled each k-mer and mapped it back to find the node that carries its annotation row. SSHash numbers a reverse-complement node as the stored node plus the dictionary size, so I subtract the offset instead. I added `DBGSSHash::get_base_node` for this. The approach is the one Harun's redone aligner uses (`alignment_redone/annotation_buffer.cpp`), and it was carried in #670.

I added a test that the keys match a per-k-mer `map_to_nodes` and agree across strands.

This is the first piece of the plan to land #670 in smaller parts.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Maps annotation keys for CANONICAL SSHash graphs without spelling each k-mer. SSHash numbers reverse-complement nodes as the stored node plus the dictionary size, so `AnnotationKeyMapper` now calls the new `DBGSSHash::get_base_node` to subtract that offset instead of spelling every k-mer and mapping it back. Adds a test that the keys match per-k-mer `map_to_nodes` and agree across strands.

This is the first piece of a plan to land #670 in smaller parts.

<sup>Written for commit 4778f792ee033c85f44e86d2f665c0dee973d190. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/703?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/703?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F703&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56e538effa8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.