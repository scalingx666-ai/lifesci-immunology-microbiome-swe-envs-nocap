# Issue

**Title:** Add option to name cached BAM outputs

## Description

## Summary
- add `--bam-file-cache-names` argument for explicit BAM cache filenames
- log which reads are cached to which BAM file
- document new caching option
- refactor BAM cache naming logic into a reusable helper
- stabilize cache directory test using a read-only temp dir

## Testing
- `cargo test`

------
https://chatgpt.com/codex/tasks/task_e_689d67582538832aba961aa7f8319b37

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `426a917845cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.