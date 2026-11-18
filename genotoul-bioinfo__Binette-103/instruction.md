# Issue

**Title:** Keep all origins when the same bin comes from several bin sets

## Description

When two bin sets produce a bin with the same contigs, the bin is kept once. Since v1.2.0, the second set was added to the origin of the discarded duplicate instead of the kept bin. So the bin listed only the first set as its origin, and it was missing from the input bin report of every other set that produced it.

### Changes
- `make_bins_from_bins_info` adds the set name to the origin of the bin that is kept.

### Tests
- New unit test for a bin shared by two bin sets. It fails without the fix.

### Notes
- This changes the `origin` column in the final report and the content of `input_bins_quality_reports/` when binners produce identical bins. The selected bins don't change.

This has been implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01fdef6a9714`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.