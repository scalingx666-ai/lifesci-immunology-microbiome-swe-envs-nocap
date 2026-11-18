# Issue

**Title:** fix: batch checks read type correctly

## Description

Batch test was not correctly setting `long_read_type` in the config file due to missing `medaka_model` parameters in the parsed arguments. Additionally, the batch mode was not checking if the long read type was valid like other CLI usage does.

- [x] refactor medaka model list
- [x] refactor long read type list
- [x] fix missing long read type in batch parsing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf906684a806`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.