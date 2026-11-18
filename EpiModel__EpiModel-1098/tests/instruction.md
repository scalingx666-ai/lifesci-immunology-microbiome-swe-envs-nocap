# Issue

**Title:** Remove renv.lock

## Description

Follow-up to EpiModel/EpiModel#1007, into `dev`.

`renv.lock` came in with #1006 and stayed behind when the `renv/` directory was removed. Nothing uses it: it is in `.Rbuildignore`, there is no `.Rprofile` activating renv, and the GitHub Actions workflows install dependencies from DESCRIPTION through `setup-r-dependencies`, which does not read it. This removes it so it does not land on main with #1007. The `dev` triggers in the workflows are left as they are.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `911099aa4ddd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.