# Issue

**Title:** Ensure concatenated reference FASTA temp file has .fasta suffix

## Description

## Summary
- add a .fasta suffix when generating concatenated reference FASTA files so mappers that require the extension accept the temp file
- add a unit test to guard the concatenated FASTA extension and content
- clean up Clippy warnings in existing code that were triggered by the new lint run

## Testing
- cargo clippy -- -D warnings
- cargo test mapping_index_maintenance::tests::concatenated_fasta_file_has_required_extension

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_6913c7de9608832a942bff48473cff78)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a641b2a1bc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.