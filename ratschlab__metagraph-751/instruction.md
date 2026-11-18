# Issue

**Title:** State three walk facts in a /traverse answer

## Description

A `/traverse` answer now states three facts of the walk that a client could not derive from it:

- An event of a label's end has `successors`: the number of successors its node has in the graph, whatever their labels. It is absent where the walk did not look at them, at the extension length and where a bound stopped the arm.
- `frontier_remaining` has `live_labels`: the distinct labels on the paths a bound stopped, beside `live_paths`.
- `cap_trigger` has `segment`: the segment of the first path the bound stopped.

The web API builds a stored graphlet from this answer. It wrote placeholder values for these three fields, and its tools showed them as measured.

All three are additions. No existing field changes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/751?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/751?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F751&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e7e5a446790`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.