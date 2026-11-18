# Issue

**Title:** ENH: Increase text size

## Description

This patch increases the labels' size by dynamically calculating the
dimensions of the canvas depending on the font and the width of the
text.



As a comparison:

# Before

![screen shot 2018-02-22 at 12 55 41 pm](https://user-images.githubusercontent.com/375307/36563897-644af93a-17d0-11e8-98c5-8694edb92688.png)


# After

![screen shot 2018-02-22 at 12 55 44 pm](https://user-images.githubusercontent.com/375307/36563901-6794362e-17d0-11e8-87f3-c5a7b84634a6.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45b1437c9e5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.