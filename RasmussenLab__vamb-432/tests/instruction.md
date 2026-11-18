# Issue

**Title:** Add figure comparing Vamb versions

## Description

Users have often installed old versions of Vamb (see e.g. results presented in Han, Wang & Zhu, Nat Commun 16, 2025)
This is unfortunate, and may be due to Conda having old versions. Maybe this doc change can convince some users to upgrade, and can be used as a reference to persuade people in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8687abd494a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.