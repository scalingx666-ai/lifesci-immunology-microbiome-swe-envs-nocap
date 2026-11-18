# Issue

**Title:** Expand descriptions of LSH-relevant arguments in README and help messages

## Description

This PR expands descriptions of arguments that use locality-sensitive hashing—to lower runtime and memory usage on especially large inputs—in the README and help messages. Namely, the PR:

- Adds technical detail to the arguments in the README, borrowing from the help messages
- Adds detail on why certain values for these arguments are recommended and reasonable in practice
- Makes minor changes to the help messages

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `895a7e3bda29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.