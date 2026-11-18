# Issue

**Title:** Add date formatting to x-axis

## Description

This PR adds date formatting to the x-axis. Previously, the charts were using the default date formatting, this forces the x-axis labels to be in `%b, %d` format, i.e. `Mar, 25` for March 25th.

Closes 

Question for @quinn-dougherty  or anyone else, this pulls in the `DATE_FORMAT` from presentation.py, should I add date format to the ~`Presentation`~ `Parameters` model?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f6fa77b78cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.