# Issue

**Title:** automatically generate markdown files and deploy Pages

## Description

Not urgent, I can make tests on a clone repository to see if it works as expected. Then we can decide if we switch to markdown for our manpages or not. 

General idea: when pushing to `dev`, GitHub Action calls a bash script to build mardown files in `./docs`, and then deploys a static website with GitHub Pages.

first attempt, assuming that GitHub Pages is active and reads `./docs`. Also assuming that `ubuntu-latest` has `perl` and `pandoc` installed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ca1412aa1cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.