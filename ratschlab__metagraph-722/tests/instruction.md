# Issue

**Title:** Reject invalid alignment counts in HTTP requests

## Description

Validate `max_alternative_alignments` before converting it to an unsigned count in `/align`. Negative values previously wrapped into large positive counts; zero silently selected one alignment. Invalid values now return HTTP 400. Omitting the field retains the configured default.

Add API regressions for invalid values across basic, canonical and primary graphs, and document the behavior change in the release notes.

Prepared with Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Rejects invalid `max_alternative_alignments` values in the HTTP `/align` endpoint instead of silently accepting them. Negative values previously wrapped into large unsigned counts, and zero silently selected one alignment; both now return HTTP 400. Omitting the field keeps the configured default.

**Tests and docs**
- Adds API regression tests covering negative, zero, null, boolean, fractional, string, and out-of-range values.
- Documents the behavior change in the release notes.

<sup>Written for commit 41c2b49b6e3c576070f5f618808c71037c3bdebe. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/722?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/722?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F722&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8545e742dc95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.