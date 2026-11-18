# Issue

**Title:** Remap annotations from a primary graph to an SSHash graph with --remap-graph

## Description

`transform_anno --remap-graph` accepted only graphs in `basic` mode. Most of our large indexes use primary graphs, so their annotations could not be moved to SSHash. It now also accepts a primary source graph with an SSHash target built with `--mode primary`.

A primary succinct graph stores each k-mer in one orientation, and its row-diff successors are edges between stored k-mers. SSHash keeps the stored k-mers as nodes 1..N and their reverse complements as N+1..2N. When the SSHash graph is built from the contigs of the primary graph (`transform --to-fasta`), both store every k-mer in the same orientation, so rows and successors carry over as in basic mode. The command stops with an error if the target stores any k-mer in the other orientation.

The result has a row for every SSHash node, including the reverse complements, like an annotation built for that graph directly.

So far this ran only on the transcripts test data, not on a production index.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/738?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/738?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F738&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `353cc00d28c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.