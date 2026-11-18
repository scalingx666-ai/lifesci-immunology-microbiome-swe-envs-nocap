# Issue

**Title:** Fixes issue with slickgrid re-rendering

## Description

This fixes an issue of category values not updating after a new metadata column is selected. The issue was a missing call to invalidate and render in the grid.

The animated GIF bellow shows the interface working again:

![issue-744](https://user-images.githubusercontent.com/375307/69687264-253b0900-1077-11ea-8e69-53829e76a18d.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ff013d1e501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.