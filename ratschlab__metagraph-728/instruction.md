# Issue

**Title:** Remove unused CLI options and fix Python client error handling

## Description

The CLI accepted `--coord-binsize`, `-f/--frequency` and `-d/--distance` and ignored them. Nothing has read these values since the coordinate mode was removed in 2023 and the old aligner path in 2019. They now fail as unknown options. No script, workflow or doc in this repository passes them.

`GraphClientJson.ready()` detected a loading server by matching the error text "503: Server is currently initializing". It now checks the 503 status, which the server returns only while it loads the index. Rewording the server message no longer breaks `ready()`. `ready()` also takes an optional `timeout`, like `stats()`.

The client's class docstring said errors come back in the second element of a tuple. The client raises `RuntimeError` and returns only the JSON response. The docstring and return annotations now say so.

Smaller changes:
- `writing-rules.json` adds `metagraph/docs/*.md`, so notes like `traverse.md` from #711 will be checked.
- `AGENTS.md` and `CONTRIBUTING.md` link `TEACHING.md` for design notes and other explanatory text.
- `tax_classifier.cpp` drops the `Error:` prefix from logger errors. The logger already marks them as errors.
- A PR template asks who needs a new option or API field, as `STEWARDSHIP.md` suggests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/728?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/728?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F728&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `175f2c28886a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.