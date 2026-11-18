# Issue

**Title:** updated config file

## Description

centralized default values. tested.

added new values: 
- Merging
- deduplication switch

changed 'true' -> True tanslates correctly to : true  in yaml file. 'true' is read as string and messes up the if statements in the Snakefile


#34

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `284be66ed1e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.