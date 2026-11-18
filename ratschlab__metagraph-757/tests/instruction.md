# Issue

**Title:** Do not limit the splits of a path unless the request does

## Description

The default of `strategy.branching.max_splits_per_path` changes from 64 to `"unlimited"`. A request can still set a number.

Why: a seed carried by thousands of records uses 64 splits within a few hundred bases, so every client had to raise the field to get an uncut answer. On the RefSeq index, an 80 bp seed in 9,387 records was cut at 244 bp with the default. With `"unlimited"` both arms completed 300 bp, in less time (14.5 s against 17.2 s).

The limit adds no bound of its own. Each split adds a path, and the paths of an arm are capped at 10,000. The caps on steps and live paths and the time budget also still apply.

The answer for a wide seed gets larger, since the paths are no longer cut (5.9 MB against 4.6 MB in the case above).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/757?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/757?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F757&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1f785fcfd55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.