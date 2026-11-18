# Issue

**Title:** Fix invalid `--gunc_database_type` options

## Description

— updates the `--gunc_database_type` enum and default to the database names actually accepted by `gunc download_db` (`progenomes_2.1`, `progenomes_3`, `gtdb_95`, `gtdb_214`, `test_data`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e59a5e894adf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.