# Issue

**Title:** Add option to filter probes with poly(A) sequence

## Description

This adds the `polya_filter` module, which is a filter on probes that contain sequence with long stretches of A bases (or T bases). It might be desirable to avoid such probe sequences, e.g., to not enrich carrier RNA.

This also adds a `--filter-polya` argument to `design.py` that, when set, applies the `polya_filter` module.

The definition of a stretch of A bases (or T bases) given as arguments with `--filter-polya`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90d7b9b45546`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.