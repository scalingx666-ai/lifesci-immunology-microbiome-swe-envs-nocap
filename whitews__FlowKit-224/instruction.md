# Issue

**Title:** use importlib for compatibility with python 3.12

## Description

Hi Scott,

it seems the newest release has undone the changes I made in #192. Since you also dropped support for Python 3.8, I removed the try except clause since there is no more fallback needed. I'm unsure why I can't find the changes in the history of the file anymore, but here we go again :)

Best,
Tristan

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd649f111b96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.