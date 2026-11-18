# Issue

**Title:** Give each graph of a list server a fair part of a /traverse request's time

## Description

. That change bounds a request on a list server to its budget once per seed, but the walks that start first can use all of it. On mex, a seed held by all 11 RefSeq files with a 15 s budget came back in 16 s. Two files walked for the full 15 s, and the other 9 started after the deadline and returned no walk.

Each walk now gets its budget or a fair part of the time left, whichever is less. The part is the time left times the pool's threads, divided by the walks of the request not yet finished. A graph without the seed finishes at once and leaves its part to the others. For the RefSeq case, each of the 11 walks gets about 2.7 s, and the request still ends near 15 s.

The manual's list-of-graphs section describes the rule.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/763?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/763?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F763&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70f9711739a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.