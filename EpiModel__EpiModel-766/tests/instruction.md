# Issue

**Title:** update ess calculation in saveout.net to work with multiple networks

## Description

Making this as a separate PR since `multinets` itself may not be merged into `main` for some time.

references EpiModel/EpiModelHIV-p#166

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `443284e27117`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.