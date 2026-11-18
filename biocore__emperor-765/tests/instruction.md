# Issue

**Title:** Fix color sorting in the legend

## Description

; see  for details on the way I fixed the bug.

Along with the fix to `DecompositionView.setCategory()`, I also added in a test to make sure that these changes remain in effect. Also made some minor code fixes in `test_decomposition_view.js`.

Hope this is useful!

![](https://user-images.githubusercontent.com/4177727/82105069-47c8e900-96ce-11ea-8bd7-baf56ef06104.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b959aed7ffcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.