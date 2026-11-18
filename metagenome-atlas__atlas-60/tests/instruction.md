# Issue

**Title:** Put deduplicate at the begining of workflow, new stats

## Description

The idea of the stats files (read_length and insert sizes) is that they can be used for assembly.

I tested the new workflow on example and realdata!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4faa17973f58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.