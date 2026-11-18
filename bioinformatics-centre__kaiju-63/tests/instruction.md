# Issue

**Title:** xargs now uses platform-agnostic -I flag

## Description

This resolves the issue with the `xargs -i` flag breaking Mac builds (#61). @pmenzel gets all the credit for the solution (see dahak-metagenomics/dahak#55).

@pmenzel if you already had a PR or commits prepared, feel free to close this PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db8f4d4f39b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.