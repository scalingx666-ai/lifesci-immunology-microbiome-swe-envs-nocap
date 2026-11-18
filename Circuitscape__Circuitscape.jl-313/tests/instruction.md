# Issue

**Title:** builder passed incorrect value to habitat_map_is_resistances,

## Description

`start()` was passing the incorrect value to `cfg["habitat_map_is_resistances"]`. Needs "true" or "false", was getting "resistances" or "conductance". Tested this locally and it seemed to work. .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83eaa1909801`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.