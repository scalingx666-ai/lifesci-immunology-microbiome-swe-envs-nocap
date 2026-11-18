# Issue

**Title:** Take the succ/pred bitmaps from the succinct graph when converting to SSHash

## Description

`transform --graph sshash` now skips SSHash's "Checking succ/pred" pass when the input is a basic succinct graph. The contig extraction already walks every node, so it reads each node's in- and out-degree from the neighbouring BOSS edges and fills the `succ_is_next` and `pred_is_prev` bitmaps directly. `DBGSSHash` takes them through a new optional constructor argument.

On the UHGG Catalogue graph (9.67 billion k-mers, k=31, 24 threads, one run each on a shared host), the conversion took 29:28 against 36:03 on master. The SSHash build went from 17:06 to 8:21 and the extraction from 17:38 to 19:59. A full-size comparison found no differing bit against the bitmaps SSHash computes.

Primary graphs and other source representations take the existing path.

Debug builds compute both sets of bitmaps and assert that they are equal. The new test compares the unitigs of a converted graph with those of a graph built from the contigs, for graphs with and without masked dummy k-mers.

Prepared with AI assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/743?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/743?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F743&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ee6e4cd379b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.