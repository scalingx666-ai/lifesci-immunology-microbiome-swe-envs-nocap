# Issue

**Title:** ENH: Add menu item to hide biplot labels

## Description

The labels can get really crowded if a lot of features are shown on screen. This PR adds a menu item to hide arrow labels, demo:

![labels](https://user-images.githubusercontent.com/375307/40754829-1dc0bb1a-6430-11e8-95fa-2f0515e7a9ed.gif)

**Note**: I've noticed that there's a problem with the label size which is obvious for taxonomic names (see in the image above), I'm working on a fix but don't really anything yet.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd53d099ae09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.