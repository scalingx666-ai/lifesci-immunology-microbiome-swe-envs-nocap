# Issue

**Title:** Use setuptools-scm for Vamb versioning

## Description

This tool will automatically set the correct Vamb version based on Git info. This is useful for several reasons:
* It makes it harder for us to mess up the versions on release
* When testing Vamb, the log file will tell us the exact commit used

Not 100% sure we really want this

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b10b2cc76257`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.