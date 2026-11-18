# Issue

**Title:** Sync hotfixes from stable to dev

## Description

This is a bit backwards from the usual workflow but we've made a few fixes directly to stable so I'd like to bring those over to the dev branch too.  This should cover a few different recent fixes:

 * #204: Scott's fix with test included for a newer Snakemake version
 * #211: Longer CircleCI stdout timeout
 * #216: Specify earlier Megahit version

Then we'll have a test-passing dev to work with again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca6992bb9042`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.