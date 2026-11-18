# Issue

**Title:** ENH:Download colormap instead of discrete legend

## Description

Previously when a continuous colormap was set and the user downloaded
the SVG image, Emperor would produce a categorical list of the values,
this PR changes this so that a colormap is produced instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a78ccce87945`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.