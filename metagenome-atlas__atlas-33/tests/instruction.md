# Issue

**Title:** generate read stats for all steps

## Description

generate read stats for all steps via the rule **read_stats**:

Other modifications to the workflow:
- Optional duplication rule instead of compress
- Control QC steps via the list _processed_steps_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59875d7ea771`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.