# Issue

**Title:** Bump the tutorials to the survival and trajectories tutorials

## Description

Adds the survival analysis and trajectories tutorials in place of the MIMIC-II survival and fate notebooks, with redirects from their old URLs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59bb1c584b49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.