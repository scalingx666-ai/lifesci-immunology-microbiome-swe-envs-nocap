# Issue

**Title:** Log server request payloads only in verbose mode

## Description

`server_query` logs complete search requests, including FASTA sequences, at INFO level. Large queries can therefore generate many gigabytes of stdout logs.

Move the request payload dump to TRACE, enabled by `-v`/`--verbose`, and skip JSON formatting when TRACE is disabled. Other INFO messages remain unchanged.

Checked with a compiled logging probe. Full server testing will follow the master CI build.

.

Prepared with Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Logs server request payloads at TRACE instead of INFO so large search queries—including FASTA sequences—no longer fill stdout with gigabytes of output.

- The full request dump is only emitted with `-v`/`--verbose`, and JSON formatting is skipped when TRACE is disabled.
- Other INFO messages are unchanged.
- .

<sup>Written for commit 458b263f1f1642852ad46cce2bb463a0a366d356. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/687?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/687?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F687&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fb1eae8ad3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.