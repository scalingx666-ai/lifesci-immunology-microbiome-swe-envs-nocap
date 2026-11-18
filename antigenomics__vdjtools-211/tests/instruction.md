# Issue

**Title:** Preserve scientific-notation Int64 counts

## Description

Scientific count text such as `9.007199254740993e15` lost one count through the Float64 fallback; scientific notation for Int64 maximum became null. Keep the existing plain-integer fast path and use native Decimal parsing/truncation for the remaining numeric text. Preserve legacy fractional truncation, booleans, nulls and invalid/out-of-range handling.

Require Polars >=1.37, the first release containing [scientific-notation Decimal parsing](https://github.com/pola-rs/polars/releases/tag/py-1.37.0). The actual shared expression passes at that minimum and at current Polars. No Python row loop or new dependency is added.

Validation: 90 reader/cohort checks and 57 CLI/mapper/budget checks pass. The new normalization and AIRR cases fail before the fix. One-core Stratos medians over 1,000,000 rows: plain integer text 42.6→45.0 ms; zero-decimal text 57.6→57.0 ms, with identical common-path results. This completes the remaining #202 edge case before 5.3.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12d3bf366ea8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.