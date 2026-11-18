# Issue

**Title:** Fix overflowing bugs

## Description

and .

GIF showing the now-slightly-fancier side panel (#173) --
![scrollbar](https://user-images.githubusercontent.com/4177727/85641798-7ed2d880-b644-11ea-97dc-dbff408597d8.gif)

GIF showing properly-overflowing long IDs (#205) --
![idoverflow](https://user-images.githubusercontent.com/4177727/85644183-1804ed80-b64b-11ea-8204-e75745371224.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ca198782e8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.