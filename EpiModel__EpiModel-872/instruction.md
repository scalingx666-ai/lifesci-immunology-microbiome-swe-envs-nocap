# Issue

**Title:** Use `collection::queue` for `attr.history`

## Description

Use `queue` (linked list) instead of R `list` to store the `attr.history` elements. This data structure massivelly reduces the cost of appending new elements to `attr.history`.
The implementation is very similar to before as the `as_list()` method allow simple conversion to a list once we want to retrieve the data.

The idea to use this structure comes from this EpiModelHIV-p function: https://github.com/EpiModel/EpiModelHIV-p/blob/DoxyPEP/R/windowed_counter.R

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9718d411105f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.