# Issue

**Title:** Removes a lot of unused CSS and improves CSS for integration with Emperor

## Description

The input's CSS declarations for Empress weren't namespaced so the style affected Emperor.

This also centers the "loading animation" on the tree not on the screen - makes things look nicer in a tandem plot.

I've also fixed #256 by making the text non-selectable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ca08b746105`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.