# Issue

**Title:** ENH: Add download scree plot button

## Description

This PR adds a button to download an SVG file of the scree plot.

This also includes a few lines that were missing from #638 (I accidentally left them out 😱 ... see controller.js).

![scree-plot](https://user-images.githubusercontent.com/375307/36329939-ca77e0d2-1335-11e8-9171-b68a50d7083c.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f391c05da12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.