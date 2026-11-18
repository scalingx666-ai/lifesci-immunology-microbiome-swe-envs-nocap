# Issue

**Title:** Refined options parser for classify_wf

## Description

Added back **options.scratch_dir** and **options.recalculate_red** in the function **parse_options** for the command _classify_wf_ to prevent an error "AttributeError: 'Namespace' object has no attribute".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19f4c3bc19e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.