# Issue

**Title:** Remove upper snakemake bound

## Description

I think this was set due to an bug in a snakemake version that has since been fixed. Current snakemake version is v7.32.3.
Though perhaps we should fix all the software versions to a known working set?

Integration tests:
- [x] test_short_read_assembly
- [x] test_long_read_assembly
- [x] test_short_read_recovery
- [x] test_long_read_recovery
- [x] test_short_read_recovery_fast
- [x] test_short_read_recovery_queue_submission

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de1a48ab0feb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.