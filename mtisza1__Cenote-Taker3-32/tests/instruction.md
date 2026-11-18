# Issue

**Title:** to v3.4.4

## Description

fixes:
- correcting logic of linear minimum length bug
- migrating to new pyhmmer logic #31 
- refactor code for pandas v3 breaking changes
- checked mmseqs2 v18 works on MacOS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef024bae1cf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.