# Issue

**Title:** Fix glitch when centering the camera

## Description

This PR fixes a problem where after re-centering the camera the whole plot would jump between locations. For example notice in this animation how after I recenter the plot *and rotate the plot*, it jumps between positions:

![old-centering](https://user-images.githubusercontent.com/375307/43019787-f634932c-8c12-11e8-8ef9-613f84cccdb0.gif)

After fixing this problem, the plot can be rotated after re-centering and there are not jumps or glitches:

![new-centering](https://user-images.githubusercontent.com/375307/43019824-0675d534-8c13-11e8-983d-54f8cc696379.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd53d099ae09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.