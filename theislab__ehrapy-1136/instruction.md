# Issue

**Title:** Keep the matplotlib backend when loading holoviews extensions

## Description

After the first holoviews-based ehrapy plot in a notebook, holoviews switched matplotlib to agg, so every later matplotlib figure (UMAPs, ranking plots, confusion matrices) silently disappeared from notebooks and the rendered tutorials.
`load_hv_extensions` now restores the user's matplotlib backend after loading the extensions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb4015055d93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.