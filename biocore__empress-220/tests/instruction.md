# Issue

**Title:** STY/BUG: Fix an issue with dropdown menus and rename IDs

## Description

Fixes an issue with drop-down menus pushing the label and checkbox in
the sidebar.

Long metadata columns would make the label and checkbox not be visible:

<img width="1679" alt="Screen Shot 2020-06-29 at 1 25 21 PM" src="https://user-images.githubusercontent.com/375307/86058050-19506480-ba15-11ea-89e9-bf1712c8b117.png">

I fixed this by setting the max width to a known value:

![fixed](https://user-images.githubusercontent.com/375307/86058071-24a39000-ba15-11ea-8202-dc4276bba1e6.gif)


Also replaces "node id" references to be "node name" (note the screenshots above were capture before I put these fixes in).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cd33d29331d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.