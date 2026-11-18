# Issue

**Title:** Search JSON: kmer_coords and kmer_abundances as strings

## Description

## Summary
Serialize `kmer_coords` and `kmer_abundances` in `SeqSearchResult::to_json` as single colon-separated strings, matching `to_string` / CLI query output instead of JSON arrays.

## Tests
- `integration_tests/test_api.py`: assert string dtype for those columns when `query_counts` / `query_coords` is used.

## Compatibility
Clients that parsed these fields as JSON arrays need to treat them as strings (split on `:` per existing CLI rules).

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c5367078e3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.