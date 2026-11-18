# Issue

**Title:** Merging testmouse branch on to master

## Description

Includes the first introduction of mouse TCRs to the script.

Includes a fix for a bug where ultra-deleted J genes (up to the terminal F residue) could occasionally end up truncating the CDR3 once it's stitched back together.

Also switches 'sys.exit()' to raised exceptions/errors, where applicable (based on ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9b1679a580e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.