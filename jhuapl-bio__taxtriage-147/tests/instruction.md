# Issue

**Title:** 146 oom error for alignment per sample

## Description

- Added retry functionality for alignment_per_sample with increasing memory needs
- Adjusted batch sizes for cross-reference comparisons during conflict regions steps
- Added slight report adjustments
- Added taxid and name to output post-minhash output files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `506a86300435`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.