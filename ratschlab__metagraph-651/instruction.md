# Issue

**Title:** Cancel superseded pull request CI runs

## Description

Cancel an older MetaGraph CI run when a new run starts for the same pull request. Group by workflow, event and PR number; use a unique run ID for other events so master/tag publishing is not interrupted or queued by this rule.

Apply concurrency once in the parent workflow so the Linux/macOS matrix continues to run in parallel. This can merge before the dependency/atomic PR stack.

Validation: YAML parsed successfully; the only configuration change is the workflow-level concurrency block.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Cancels an older MetaGraph CI run when a new run starts for the same pull request. Non-PR runs for branches or tags, and runs for different refs, stay independent, and the Linux/macOS build matrix still runs in parallel.

The concurrency rule only cancels superseded pull request runs and is applied once in the parent workflow so reusable workflows don't cancel sibling matrix jobs.

<sup>Written for commit 269a683154ef03653d9eba37efc8ec61eb69704f. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/651?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/651?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F651&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de7766ee4454`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.