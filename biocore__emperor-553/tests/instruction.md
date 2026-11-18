# Issue

**Title:** PERF: Lazily load large studies to improve performance

## Description

When matrices with more than 1000 samples are loaded in emperor, none of the tabs are "active" (meaning that there is no table of colors, shapes, scales, etc) until a metadata category is selected for each of the controllers. After a metadata category is selected, the grid with the colors, shapes or scales is displayed, and the program should continue to work as usual.

Making these changes allows us to load the EMP (~30K samples) in about 7-10 seconds, the memory consumption is greatly reduced and the overall experience is smoother.

In making these changes, I had to make a few additional changes:

- Sort metadata headers alphabetically.
- Make the `setEnabled` method disable the widgets in the current view controller.
- Allow for `setMetadataField` to take `null` as a parameter, this in turn resets the class' attribute to its default state (for example in `ColorViewController` all markers are changed back to red, in `ScaleViewController` all markers are changed back to have a scale of 1, etc).
- Allow fromJSON and toJSON to deal with `null` values.
- Add tests for all these changes 📓.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee267cce03e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.