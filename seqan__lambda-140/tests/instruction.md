# Issue

**Title:** Add reduction from DNA5 to DNA4

## Description

Added nucleotide reduction from DNA5 to DNA4 with view convert_n. I decided to keep the view convert_n a deep view by definition since it does not make sense to apply it in any context to an outer range of ranges.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c12a503a326`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.