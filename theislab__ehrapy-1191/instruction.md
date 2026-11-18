# Issue

**Title:** Draw horizontal error bars and the reference line at 0 in cox_ph_forestplot

## Description

`ep.pl.cox_ph_forestplot` draws the confidence intervals horizontally, puts the reference line at a coefficient of 0 (hazard ratio 1) instead of 1, and gives the header its own row, so that the plot reads like a forest plot again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01b210e4985b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.