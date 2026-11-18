# Issue

**Title:** Re-organize documentation

## Description

Adds missing documentation for the feature_mapping_file parameter and re-organizes the main documentation page. We now directly point to nbviewer with all the example notebooks. See the screencapture below (the Notebooks tab points to this [link](https://nbviewer.jupyter.org/github/biocore/emperor/tree/new-api/examples/)).

![screen shot 2018-09-28 at 10 53 37 am](https://user-images.githubusercontent.com/375307/46224996-d4157500-c30c-11e8-90e8-db2f46572445.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f5d0618e6f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.