# Issue

**Title:** Share a /traverse request's time across the graphs of a list server

## Description

On a server with a list of graphs, each graph's walk of a seed got the full `bounds.time_budget_ms`. The walks run on the server's thread pool, so a request could take the budget several times per seed. On staging, a seed held by all 11 RefSeq graph files took 92 s on a 15 s budget, and 158–174 s on a 30 s budget.

The manual already says a request can take the budget once per seed. This change makes list servers keep that promise. The request gets one deadline at the start: the budget times the number of seeds. Each walk gets its budget or the time left, whichever is less. A walk that starts after the deadline stops at once with the time-budget cap, so the client sees which walks were cut. A server with one graph is unchanged.

The integration tests use graphs whose walks finish in milliseconds, so they cannot show the deadline. I will check it on mex with a throwaway server on the RefSeq files after the image is built.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/761?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/761?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F761&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e7322a32e12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.