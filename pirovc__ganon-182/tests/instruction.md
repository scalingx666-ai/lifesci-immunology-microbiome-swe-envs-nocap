# Issue

**Title:** Feature/fixes clean up

## Description

- README typo
- remove old db converting scripts
- fix online tests
- update libs to latests stable releases
  - seqan3: 3.1.0-rc.1
  - Catch2: 2.13.7
  - cxxopts: 3.0.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc7dcdce590e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.