# Issue

**Title:** Report full target coverage when an alignment crosses records

## Description

When an alignment crosses from one record into the next within a column, `metagraph align` reports each record after the first as k − 1 bases too short. This affects both the TSV coordinate field and the JSON `nt_coords`.

Master's own fixture shows it. `LabeledAlignerCoordTest.CrossBoundaryThreeSequences` (k = 5) aligns `TTCGACGT|ATGCAGCT|GGGCGCAT` against:
- seq1 `GCGCTTCGACGT`
- seq2 `ACGTATGCAGCT`
- seq3 `AGCTGGGCGCAT`

The query contains all of seq3 (`AGCT` + `GGGCGCAT`), but master reports `seq3/12:1-4`. In `TestAlignCoordToHeader`, `q_concat` covers every k-mer of seq2, yet master reports `seq2/12:1-8`. Since these ranges exist so that callers can compute the fraction of each target covered, the result is wrong.

The cause is in `split_coords_by_target`. Coordinates count k-mers. At a boundary, the alignment's next k-mer is the next record's first k-mer, and that k-mer reuses the last k − 1 bases already counted. The loop subtracted the whole span from the remaining length, so those k − 1 bases went missing. With the fix:
- the shared bases count in both records;
- the loop stops when the alignment ends inside a record.

I updated the expected values in the existing unit and integration tests, and added a test for alignments shorter than a k-mer at a record's end.

I found this while assessing #670, which carried the same fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes `metagraph align` reporting each record after the first as k − 1 bases too short when an alignment crosses record boundaries, in both the TSV coordinate field and the JSON `nt_coords`. Shared boundary bases now count toward the covered range of both records, so output ranges reflect full target coverage.

**Bug Fixes**

- Sprint `split_coords_by_target` now stops when the alignment ends inside a record and attributes the k − 1 shared bases to both records.
- Updated existing unit and integration test expectations and added coverage for alignments shorter than a k-mer at a record's end.

<sup>Written for commit c7dbc53b0a8093a8e5fb917708df47bab7d11ff9. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/706?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/706?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F706&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56e538effa8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.