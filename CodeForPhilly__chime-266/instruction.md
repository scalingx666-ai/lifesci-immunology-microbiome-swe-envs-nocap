# Issue

**Title:** Slider bar code cleanup

## Description

Added a unique key parameter to the Projected Admissions and Projected Census sliders so they can display the same label. Also replaced shorthand with min_value, max_value, and value parameters.

There is a current issue with the slider where it keeps reverting to the default value. Steps to reproduce: move the slider to a different value, click the checkbox to Show Daily Counts, and then uncheck the box. The slider will revert to its default value. Some more information in the below link. Any suggestions for a fix appreciated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96d505106035`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.