# Issue

**Title:** Add/gtdb tree

## Description

- wrapped trees into subwf
- added itol files generation
- added gtdb align and gtdb identify
- added subwf hotfix for new trees. Files will have 'full' in name. I hope workflow would not be launched with that subwf and we will remove it in next release

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d00c13827c42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.