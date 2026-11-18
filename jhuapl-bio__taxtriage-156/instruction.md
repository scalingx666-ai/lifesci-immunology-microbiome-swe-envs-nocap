# Issue

**Title:** 154 minimap2 alignment memory allocation leads to oom error

## Description

- Dropping ram use for mmap2 to 60% in container
- Update retry strategy as integers in modules.config rather than strings

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c998e6f89afc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.