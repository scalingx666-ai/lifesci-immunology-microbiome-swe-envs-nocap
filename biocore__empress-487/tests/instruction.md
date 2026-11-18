# Issue

**Title:** Use ancestor information in taxonomy feature metadata (only computing ancestor info in the JS interface)

## Description

This is an alternate version of #482 that avoids dramatically increasing the size of the taxonomy information stored in the QZV -- instead, each entry in the feature metadata is "expanded" as needed in the JS. This means that in the worst case (visualizing the lowest level of a taxonomy, e.g. "Level 7" / species) we just need to stitch back together the original taxonomy for every tip described in the feature metadata (this process could be made more efficient -- see comment added in a95b652).

This works by passing a list of the "split taxonomy columns", in descending rank order (i.e. `Level 1`, `Level 2`, ...) from the Python to the JS code, which (in certain contexts) uses this list to determine how much if any ancestor data to get for a given feature metadata column. Doing things in this way may make life easier in the future, since it'll let us name the taxonomy columns (after creating them) whatever we want, so we can do things like use 0-indexing / use a different term than `Level` / etc. if desired without breaking this functionality.

As with #482, this  and .

![fancy](https://user-images.githubusercontent.com/4177727/108157893-a75a8780-7098-11eb-9adb-87363cad2de1.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e543610c5654`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.