# Issue

**Title:** Fix nextflow lint errors and warnings

## Description

## Summary
- Fix `nextflow lint` errors and warnings in local pipeline files
- Add missing `def` declarations for undeclared variables (`seq_type_ok`, `data_type_ok`, `bam_count_ok`)
- Move `+` string concatenation operator from start of line to end of previous line (parse error)
- Replace deprecated `Channel` with `channel` factory calls
- Replace deprecated implicit closure parameter `it` with explicit named parameters
- Prefix unused workflow parameters with `_` to suppress warnings

## Test plan
- [x] `nextflow lint .` passes with 0 errors and 0 warnings
- [x] `nf-core pipelines lint` passes with 0 failures
- [x] No changes to nf-core modules or subworkflows (only local files modified)
- [ ] CI pipeline tests pass

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e899b2c9dc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.