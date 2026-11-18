# Issue

**Title:** Fix compute_r_eff() error message

## Description

If you pass an unrecognized method name to _.compute_r_eff()_ it raises an exception having the following error message: 'Method must be "daily", "**infected**", or "outcome", not "{method}"', but the accepted method names are "daily", "**infectious**" and "outcome".

This pull request fixes the error message.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a55a849b2a16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.