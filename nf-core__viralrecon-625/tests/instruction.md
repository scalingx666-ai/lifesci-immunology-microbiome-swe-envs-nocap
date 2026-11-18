# Issue

**Title:** Fix .str accessor crash on single-value AD in variants long table

## Description

`bcftools_bcftools_query_to_table` assumed every artic_minion `AD` value was a comma-separated `REF,ALT` pair. When clair3 emits a uniformly single-valued `AD` column, pandas infers a numeric dtype and `table["AD"].str.split()` raises `Can only use .str accessor with string values!`. This surfaced on `test_full_nanopore` but not `test_nanopore`, purely due to input data.

Cast `AD` to string before splitting and reindex so `REF_DP`/`ALT_DP` always exist, mapping a lone value to `ALT_DP`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cbb764e3801`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.