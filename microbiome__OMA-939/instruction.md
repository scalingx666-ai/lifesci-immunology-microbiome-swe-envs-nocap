# Issue

**Title:** Say which columns addQC() adds (contribution to #934)

## Description

Contribution to #934 (`fix/914-addqc`).

#934 already replaces the deprecated scuttle QC functions with `mia::addQC()`, and does so more completely than the earlier version of this PR did. This PR now adds only one thing on top of it: the QC chapter says what `addQC()` adds to `colData`:

> The total counts per sample can be calculated using `addQC()` from mia. It adds the library size (`total`) and other sample-level metrics to `colData`.

The later code uses the `total` column, so this tells readers where it comes from.

The `update.tree = TRUE` fix in `taxonomy.qmd` that was here before is dropped: it is in `devel` since #918 was merged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea0083d51bda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.