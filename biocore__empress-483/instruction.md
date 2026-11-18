# Issue

**Title:** New color map

## Description

This PR adds a new custom diverging color map (green to light orange to purple) that is great for coloring tree branches as a lot of the other diverging color maps are either hard to see the separation of values and/or the middle values are colored to light which makes the branches hard to see. 
![log_ratio](https://user-images.githubusercontent.com/28127694/107468034-1c1f4600-6b1c-11eb-9c7c-695f33644887.png)
You can see that this color map does a good job separating the two extreme values (i.e. endpoints) from the middle values while still making everything visible on screen.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d14e07d7477`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.