# Issue

**Title:** fix: remove check for header by sniffer

## Description

The `csv.Sniffer`'s `has_header` method produces false negatives. Since we anyway check for the presence of columns, we can simply remove this check.

Fix #226

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ab5c64f94ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.