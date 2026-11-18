# Issue

**Title:** Map oriented nodes to annotation rows in one place

## Description

Add `AnnotationKeyMapper`, which returns the node whose annotation row an oriented node uses. In basic graphs that is the node itself. For a `CanonicalDBG` it is the base node, and in canonical graphs it is the canonical k-mer's node. The existing aligner's annotation buffer now uses it instead of its own mapping. Unwrapped primary graphs are rejected, as the buffer already assumed (it asserted `BASIC` there).

This is split out of #670, where the traversal and both aligners share the mapper, so that #670 and #672 can build on it independently. The SSHash fast path (`DBGSSHash::get_base_node`) is left out: that method does not exist on master yet and comes with #672, which adds the fast path when it adopts the mapper.

For every graph mode the buffer accepts, the mapping matches the code it replaces. `CanonicalDBG` only wraps primary graphs, so the old check on the wrapped graph's mode and the mapper's check on the wrapper's own mode agree.

A new unit test, `tests/graph/test_annotation_key_mapper.cpp`, covers basic graphs, the rejection of unwrapped primary graphs, and, for DNA, that both strands of a path map to the same keys in canonical and wrapped-primary graphs.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Replaces the annotation buffer's inline node-to-annotation-key mapping with a shared `AnnotationKeyMapper`, so the traversal and both aligners can reuse it in upcoming work (#670, #672).

- The mapper returns the node itself in basic graphs, the base node in `CanonicalDBG`, and the canonical k-mer's node in canonical graphs, spelling the path when needed.
- Unwrapped primary graphs are now rejected explicitly instead of asserted during fetching, matching how the test helper builds primary graphs wrapped in `CanonicalDBG`.

Adds unit tests covering basic graphs, primary-graph rejection, and both strands of a path mapping to the same keys in canonical and wrapped-primary graphs. The primary- and canonical-graph tests run for DNA only, since building those graphs for the protein alphabet crashes.

<sup>Written for commit 13684d8dee1a065de5670f97a3727e476f1c3e2b. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/683?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/683?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F683&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `490cb66b74b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.