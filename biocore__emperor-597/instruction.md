# Issue

**Title:** Improve functionality discoverability

## Description

This PR adds tooltips to lots of UI elements:

- Attribute editors in every tab now change mouse type when the mouse hovers over.
- Editors are now activated with one click (I've left out the updates for the scale in visibility in #596).
- The scree plot now shows a tooltip with the percent explained value.
- Tabs display help text when hovering over them.

This GIF tries to showcase most of these:

![tooltips](https://user-images.githubusercontent.com/375307/29437258-67e4bad2-8364-11e7-8dfa-ee90b1a232d1.gif)

Related to #586.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `604b4e9bece0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.