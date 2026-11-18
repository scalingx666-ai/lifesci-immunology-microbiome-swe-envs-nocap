# Issue

**Title:** Remove the commented-out duplicate bin check

## Description

The duplicate bin check in `parse_bin_directories` and `parse_contig2bin_tables` has been commented out since bins became dicts, and it can't work as written. Duplicate bins are already merged in `make_bins_from_bins_info`, so the dead code is removed.

### Changes
- Remove the two commented-out blocks.
- Fix the docstrings, which still said a warning was logged and that `Bin` objects were returned.

This has been implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01fdef6a9714`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.