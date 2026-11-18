# Issue

**Title:** Fix clicking on nodes not in table; refactor and test node selection menu; fix "Add" button

## Description

. Now, clicking on a tip not in the table shows text to the user explaining the situation:

![image](https://user-images.githubusercontent.com/4177727/96942454-095c0500-148a-11eb-856f-7f9fab708722.png)

Similarly, clicking on an internal node where none of its descendant tips are in the table also shows a note:

![image](https://user-images.githubusercontent.com/4177727/96942502-285a9700-148a-11eb-93f6-06ec440a9f18.png)

This also refactors the node selection menu a decent amount. Mainly, I realized while working on #314 that a lot of the showing / hiding operations in the menu rely on some pretty complex logic and were done in a very ad-hoc way (this is primarily my fault lol), so I tried to make things more manageable. Now, more of the work is delegated to `makeFeatureMetadataTable()` / `makeSampleMetadataTable()`, so life should be easier. This PR also adds some tests for the menu -- these are by no means comprehensive, but they should be a good start.

While I was at it, I also fixed #272 and added a test for it.

Last change worth noting, I think, is that I removed `SelectedNodeMenu._checkTips()`. When more than a few tips were not present in the tree, the toast messages shown were kind of hard to read (see below); furthermore, it looks like the tip keys rather than names were being shown, anyway, which makes interpreting these messages hard for users. Since the revamped menu now has the ability to show these sorts of warnings a lot more cleanly, I delegated this to there.

_Before:_
![b42](https://user-images.githubusercontent.com/4177727/96943883-37dbdf00-148e-11eb-92a6-0a5f0e5bcd47.png)


_After:_
![yeeee](https://user-images.githubusercontent.com/4177727/96943811-095e0400-148e-11eb-8ee8-a85e75ff5eda.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e982e65b5983`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.