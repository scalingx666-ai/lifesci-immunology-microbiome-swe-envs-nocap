# Issue

**Title:** Exit with status code 1 in case of an error - fatal warning

## Description

The tests inside the component tests pipeline was failing but the workflow itself wasn't: https://github.com/merenlab/anvio/actions/runs/26166457784/job/76971855168

I updated the exit code for error - fatal warning cases so that any tooling wrapping anvio will be able to understand something is wrong. The workflow fails properly now: https://github.com/merenlab/anvio/actions/runs/26168320675/job/76978629756

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05a6470ccd51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.