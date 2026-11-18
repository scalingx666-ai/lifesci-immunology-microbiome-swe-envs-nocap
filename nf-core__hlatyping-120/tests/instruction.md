# Issue

**Title:** Remove social preview image to use GitHub OpenGraph

## Description

GitHub now generates OpenGraph images: https://github.blog/changelog/2021-04-21-opengraph-images-for-github-repositories-commits-issues-and-pull-requests/
Using this OpenGraph possibility will convey more information in a nicer way so we're ditching the social preview images.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8487a0610041`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.