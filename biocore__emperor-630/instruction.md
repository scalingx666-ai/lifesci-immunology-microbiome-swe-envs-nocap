# Issue

**Title:** ENH: Copy sample names to clipboard.

## Description

Users can now click or double-click to copy a sample's name. If clicking
on a sample, they'll need to also click on the banner at the bottom
left. If double clicking on a sample, the name is automatically copied
to the clipboard.

### Example

First clicking on a sample then on the legend to get the text. And another example double-clicking a sample to get the text.

![click-and-double-click](https://user-images.githubusercontent.com/375307/33401260-894f66fe-d50d-11e7-8e6b-c25a9c46a224.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a97f7a654636`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.