# Issue

**Title:** Generate zipped OTU table fixtures in renew tests

## Description

## Summary
- generate the zipped gzip OTU table fixture on the fly inside test_renew instead of storing a binary archive
- restore the original renew CLI tests and add dedicated coverage for --input-zipped-gzip-archive-otu-table for both executables
- remove the checked-in renew_archive_tables.zip test asset

## Testing
- pixi run -e dev pytest test/test_renew.py

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_6949b8ee52b4832a9ddb347aecdd09ad)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e5b8847323c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.