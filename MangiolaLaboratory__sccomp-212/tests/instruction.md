# Issue

**Title:** Add pkgdown workflow for R package deployment

## Description

- Introduced a new job in the GitHub Actions workflow to build and deploy the pkgdown site.
- Configured steps for R environment setup, installation of dependencies, and CmdStan.
- Added deployment steps to upload the generated site artifacts to GitHub Pages.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ef5a77fdba9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.