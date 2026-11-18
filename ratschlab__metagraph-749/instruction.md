# Issue

**Title:** Serve /traverse on a server with a list of graphs

## Description

`POST /traverse` was served on a single-index server only. A server started with a list of graphs now serves it too, in the way `/search` does.

- The `graphs` field selects graphs by name, with the same rule as `/search`: without it, every graph of a list with at most 10 names is used.
- Every selected graph is walked in the server's graph pool.
- Each entry of `results` holds `walks`: one walk per graph that has the seed and at least one of its labels. A walk has the fields of a single-index answer and the name of its `graph`.
- A graph adds no walk when it lacks a k-mer of the seed, has none of the named labels, or has no label on every k-mer of the seed. This matches a graph without hits in `/search`.
- A named label that no selected graph has is refused with HTTP 400.

The answer of a single-index server does not change. It still refuses `graphs` as an unknown field.

The prototype branch walks one graph file per request and wraps the answer in an envelope with attempt and deadline fields. This PR follows `/search` instead, so both routes share one selector and no request names a file path.

Load: a request occupies one thread of the graph pool per selected graph, each for at most seeds × time budget. A `/search` request on the same server occupies the pool in the same way. There is no cap on the number of graphs per request, as in `/search`.

The manual page has a new section, "A list of graphs".

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/749?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/749?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F749&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13e17ada8141`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.