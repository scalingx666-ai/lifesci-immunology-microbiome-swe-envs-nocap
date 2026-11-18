# Issue

**Title:** BUG: Fix problem with gradients

## Description

Gradients would fail to display when the "show continuous" button was pressed. The problem was manifested when the data was split into numeric and non-numeric data (missing data), some values were incorrectly cast to numbers, and if a value was cast from `'1.0'` to `1`, this object would later not be found anywhere and an error would be thrown. I changed the function to return unmodified objects, and perform the casts to numbers only when needed (I also added a few extra tests).

Thanks to @cuttlefishh and @amnona for reporting this problem.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3c420a01fee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.