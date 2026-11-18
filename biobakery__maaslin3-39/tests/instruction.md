# Issue

**Title:** Miscellaneous small changes

## Description

## Description

This PR includes a few small tweaks for the convenience of users and developers:

1. It changes the formatting of timestamps in logs to be consistently limited to hundredths of a second. That makes the timestamps easier to read and a consistent width.
2. It adds reformulas to the Imports, reflecting the same change in lme4. `reformulas` is used for the `findbars()` function, which used to live in `lme4`. This avoids a warning when the package is loaded.
3. Adds `maaslin3.Rproj` to .gitignore to avoid messages for developers working with the repo in RStudio.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0af79cb50183`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.