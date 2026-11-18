# Issue

**Title:** Honor SPDLOG_LEVEL in the CLI

## Description

`main()` resets the logger to INFO after initialization, so `SPDLOG_LEVEL=warn`, `off`, or `trace` is ignored by the CLI.

Preserve the initialized log level unless `-v`/`--verbose` explicitly selects TRACE. With no environment setting, the default remains INFO. Document the precedence and add CLI regression coverage.

Prepared with Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Makes the CLI honor `SPDLOG_LEVEL` instead of resetting it to INFO after initialization.

Previously, `main()` forced the logger to INFO, so `SPDLOG_LEVEL=warn`, `off`, or `trace` had no effect. Now the environment variable is preserved unless `-v`/`--verbose` is explicitly passed, which selects TRACE. The default stays INFO when the variable is unset, empty, or invalid. Documents the precedence and adds CLI regression tests covering level filtering, case-insensitivity, verbose overrides, and exit status preservation.

<sup>Written for commit 155e5b7665d14a26ba2140ec8af6e570068e5310. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/688?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/688?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F688&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e23cccec85b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.