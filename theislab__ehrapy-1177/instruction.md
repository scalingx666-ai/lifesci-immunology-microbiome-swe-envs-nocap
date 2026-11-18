# Issue

**Title:** Keep the rows of plot_cohort_barplot apart when showing it

## Description

CohortTracker.plot_cohort_barplot with show=True leaves the legend out of the tight layout and reserves its width on the right, so that tall legends no longer collapse the rows of tracked cohorts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5b2df73689a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.