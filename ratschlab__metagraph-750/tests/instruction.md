# Issue

**Title:** Let a /traverse request set the split limit of a path

## Description

A path of a `/traverse` walk could split 64 times, a fixed limit. A seed with thousands of labels uses 64 splits within a few hundred bases, because every position where some labels leave on another base is a split of the path. On the RefSeq index, a seed followed in 9,387 records stopped at 244 bp for this reason.

The request can now set the limit:

- `strategy.branching.max_splits_per_path` takes an integer up to 1,000,000 or `"unlimited"`. The default stays 64.
- It is read and echoed like `max_label_branches`.
- The fixed caps on steps, paths and live paths per arm and the time budget still bound the walk.

No fixed number fits both a walk of two records and one of several thousand, so this is a request field and the default is unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/750?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/750?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F750&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e7e5a446790`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.