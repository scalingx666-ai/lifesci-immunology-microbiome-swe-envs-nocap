# Issue

**Title:** Require distinct record headers for --index-header-coords

## Description

**Behaviour change:** `metagraph annotate --index-header-coords` now fails, and writes no `.seqs` file, if any record header in an input file is:
- empty,
- not valid UTF-8, or
- repeated within the file.

It also refuses `--header-delimiter` and inputs that are not FASTA/FASTQ. The same header may still appear in different files.

Before, consecutive records with the same header were merged into one entry, and other repeats were stored as separate entries with the same name. Either way, a coordinate could not be traced back to one record by its header. Indexes built from inputs with repeated headers need their inputs fixed before `--index-header-coords` is rerun.

I also fixed a bug on the same path: under `--header-comment-delim`, a record without a comment picked up the previous record's comment.

The code is Gunnar's, from `gr/labeled-traversal` via #670. I took only the checks and the duplicate scan, not the header lookup that traversal adds. Tests:
- unit tests for the duplicate scan and for `utils::valid_utf8`;
- an integration test for distinct, repeated (consecutive and apart) and empty headers, and for `--header-delimiter`.

The docs in `quick_start.rst` describe the new requirement.

This is the second piece of the plan to land #670 in smaller parts.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Requires distinct, non-empty UTF-8 record headers for `metagraph annotate --index-header-coords`. The command now fails, writing no `.seqs` file, if any header in an input file is empty, not valid UTF-8, or repeats within the file; the same header may still appear in different files. The check covers every record, including those too short to have k-mers. Non-FASTA/FASTQ inputs and `--header-delimiter` are refused.

Before, consecutive records with the same header were merged into one entry and other repeats were stored as separate entries with the same name, so a coordinate could not be traced back to one record by header. Also fixes a bug on the same path where, under `--header-comment-delim`, a record without a comment picked up the previous record's comment.

<sup>Written for commit 0a8feace0d2efeb3c48a6d20448c581b493156f2. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/704?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/704?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F704&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56e538effa8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.