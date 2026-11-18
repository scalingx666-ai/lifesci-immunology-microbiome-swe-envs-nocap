# Issue

**Title:** Fix that weird overlapping CSS bug in Empire plots

## Description

.

Also updated the screenshots/GIFs of Empire plots in the README, since this visual error was present in these as well. And added a small footnote to part of the README giving a caveat about the ignore absent tips setting, since I realized this could be confusing in some cases.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be98c953df9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.