# Issue

**Title:** Position Empress and Emperor exactly next to each other and add a clear dividing line

## Description

This doesn't close any of the currently-open issues (if anything it *adds* slightly more CSS), but it makes tandem plots look a lot prettier. (It also gets rid of that scrollbar that kept showing up in tandem plots.)

Before: (note the gap in the middle of the screen, and the scrollbar on the right edge)
![image](https://user-images.githubusercontent.com/4177727/86992603-b0749500-c156-11ea-9c83-6732996a8188.png)

After:
![image](https://user-images.githubusercontent.com/4177727/86992397-4360ff80-c156-11ea-8fee-0663ffee28c3.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `852e39933ac9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.