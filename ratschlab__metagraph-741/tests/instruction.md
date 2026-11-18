# Issue

**Title:** Convert a graph to SSHash with its row map (transform --graph sshash, --to-fasta --row-map)

## Description

`transform --graph sshash` converts a graph in basic or primary mode to SSHash. It also writes `<OUT>.rowmap`, so `transform_anno --remap-graph` skips matching the rows of the two graphs.

`transform --to-fasta --row-map` writes the same row map with the contigs. Use it to build the SSHash graph in a separate step, for example on another machine.

An SSHash graph numbers its k-mers in the order of its input file. The extraction already knows the source node of every k-mer it writes. So the row map is known while the contigs are written.

- The converter runs the `--to-fasta --row-map` extraction into a temporary directory, then the SSHash build.
- A row map from `--row-map` is valid only for an SSHash graph built from exactly the written file. The remap checks a sample of rows before it uses the map.
- Canonical graphs are rejected.
- The on-disk bucket writer from #737 is now the class `RowMapWriter`. The remap and the extraction both use it. The remap's output is unchanged.

In earlier runs, matching the rows took about 33 of 83 min for UHGG (33 billion k-mers, 64 threads) and 76 of 179 min for 1,000 SRA studies (32 threads). On the test graphs the written row map is byte-identical to the matched one.

Prepared with AI assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/741?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/741?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F741&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae814f0a802c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.