# Issue

**Title:** Welcome to flatland (add 2D plots)

## Description

Adds the ability to hide the third axis of an ordination. This can be achieved by going to the Axes tab, clicking in the dropdown menu for the third axis and selecting "Hide". When this happens the elements on screen are relocated to all lie in 0 in the Z axis. If ellipsoids are present, these are flattened. Animated gif of the UI changes:

![costello-2d](https://user-images.githubusercontent.com/375307/29655470-009c44ce-8866-11e7-9513-6fd1b7f936c4.gif)

As a side note, this PR also transitions the camera from a [Perspective Camera](https://en.wikipedia.org/wiki/Perspective_(graphical)) into an [Orthographic Camera](https://en.wikipedia.org/wiki/Orthographic_projection). This will help with plots included in papers, as the pictures will look flatter. Comparison of two plots showing the "keyboard dataset", note both are 3D plots:

## Perspective Camera (3D)
![screen shot 2017-08-24 at 12 53 19 am](https://user-images.githubusercontent.com/375307/29655682-af6a1a1c-8866-11e7-8755-a918a702e8c0.png)

## Orthographic Camera (3D)
![screen shot 2017-08-24 at 12 53 26 am](https://user-images.githubusercontent.com/375307/29655697-b588df64-8866-11e7-9b47-0248c0a05ad5.png)

CCing @josenavas as he came up with the original idea for the implementation 👍

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `604b4e9bece0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.