# Issue

**Title:** Keep inline matplotlib figures after the first holoviews plot

## Description

The holoviews extensions now load the user's matplotlib backend before holoviews switches it to agg, so matplotlib figures keep displaying inline in notebooks after a holoviews-based ehrapy plot, even when that plot runs before the first matplotlib figure and without `%matplotlib inline`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c9169f3d0c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.