# Issue

**Title:** fix for updated bioconductor and added shinyapps.io help to README.md

## Description

Fix to app.R to account for bioconductor's altered method of install. Also made a suggested change to README.md to deal with setting bioconductor as a repo to allow reconnect and shinyapps.io to deal with Bioconductor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81d784d8b1ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.