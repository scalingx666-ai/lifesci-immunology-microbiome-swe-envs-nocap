# Issue

**Title:** Create build-and-check.yaml

## Description

This adds a new GitHub action for building and checking the project. It's based on the `R CMD check` one from `usethis`.

It catches the problem from  unlike the current [R-CMD-check](https://github.com/statdivlab/radEmu/blob/main/.github/workflows/R-CMD-check.yaml) workflow. And so, I'm of the opinion that this workflow should probably replace that one.  If you're in agreement @adw96, I can swap them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f32233108a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.