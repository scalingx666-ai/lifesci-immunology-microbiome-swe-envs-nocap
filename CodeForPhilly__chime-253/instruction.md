# Issue

**Title:** Sets rounding for new admissions graph to ceil.

## Description

Do we want to use ceil for both the admissions graph pop-ups and the "peak" blurbs below the graph? If so, then this fix should be okay.

I didn't change anything about the admitted patients graph, because this is already ceiled in models.py:166

This change in rounding changes slightly how the peak day is calculated, possibly moving it ahead by a day or two. See the variable `on` from`chart_descriptions` in `charts.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `452df4e38206`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.