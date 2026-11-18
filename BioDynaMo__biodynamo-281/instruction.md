# Issue

**Title:** Fix issue with markupsafe which breaks nbconvert and thus the website

## Description

The latest version of markupsafe removed `soft_unicode` which is used by jupyter's nbconvert.
Therefore, we hardcode the markupsafe version which still contains the symbol.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5c009ea440f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.