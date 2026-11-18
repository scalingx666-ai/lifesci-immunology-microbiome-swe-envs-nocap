# Issue

**Title:** Include external figures in subdirectory

## Description

This will hopefully address the missing figures in #1070.  I believe that #1072 removed the two missing map figures that were previously on the external resources branch.  However, none of the vaccine map figures are being committed after they are regenerated every night.  That's why the two missing maps weren't added back.

This generalizes the file pattern of image files that are committed in the nightly external resources workflow so that the maps subdirectory is included.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3566b19d3222`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.