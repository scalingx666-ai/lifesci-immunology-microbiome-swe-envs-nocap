# Issue

**Title:** "Match" table, tree, and sample metadata, and verify that things seem ok

## Description

. Now, the sort of case described there will trigger the following error:

![image](https://user-images.githubusercontent.com/4177727/78716758-599bbd00-78d4-11ea-8cf6-2aba325fb336.png)

We will still need to match/validate feature metadata (e.g. taxonomy) when we add support for that in to Empress (#130) -- I haven't done that in this PR, but I can add it in if you'd like. (Wasn't sure how we'd prefer to handle feature metadata, so I haven't included this here.)

Also changed in this PR: I moved the QZAs/etc. needed for the moving pictures example back into the repository (in `docs/moving-pictures/`), and added a `make docs` command that'll re-generate the `empress-tree.qzv` visualization linked from the README. We could make running `make docs` part of the Travis build in the future if desired, as a de facto "integration test" (of course, this would require us to have QIIME 2 installed on Travis, which would slow down builds by a few minutes).

Thanks! Let me know if you'd like to go over this over Zoom or whatever sometime.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb25912389b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.