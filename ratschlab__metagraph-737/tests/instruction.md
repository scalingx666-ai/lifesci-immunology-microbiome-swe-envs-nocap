# Issue

**Title:** Build and read the --remap-graph row map on disk

## Description

`transform_anno --remap-graph` held the row map in memory. Moving the UHGG annotation (33 billion rows) to an SSHash graph peaked at 249 GB, of which the map was 145 GB. The map is now built and read on disk. It follows `--disk-swap`, like other `transform_anno` temporary files.

- The graph walk appends each (source row, target row) pair to one of up to 256 bucket files, by source-row range. Each bucket is then placed in memory and written at its offset in the row map file.
- The rewrite reads the row map file through one buffered reader per thread. Row-diff successors are first marked by source row, so every pass reads the map in row order.
- `--disk-swap ""` keeps the in-memory route. The temporary files take about twice the size of the row map.

Measured on UHGG on Euler with 64 threads: peak memory went from 249 GB to 107 GB. Building the map took 33 min and the rewrite 50 min, against 60 min and 40 min in memory. The runs used different nodes, and the two on-disk phases were timed in separate jobs. The result answers a query sample of 5,111 contigs the same as the old index.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/737?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/737?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F737&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9851ef8c29b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.