# Issue

**Title:** Maaslin3 code cleanup

## Description

1: Changed for loop for all R files in the folder it just loops through the list ("fit.R", "utility_scripts.R","vis.R")  

2: Take all of the following for loops  + condense them + move them to R/maaslin3.R#L47.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad592f9c5f2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.