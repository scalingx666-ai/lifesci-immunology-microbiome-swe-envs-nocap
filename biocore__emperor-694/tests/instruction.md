# Issue

**Title:** BUG: Fix version conflicts with Jupyter deps

## Description

Fixes a problem where Jupyter's require declarations would shadow
Emperor's. Specifically while using the newest version of the Jupyter
notebook jquery would be updated to version 3.x and that version is not
compatible with several dependencies of Emperor.

For now this fix ensures that there will be no version conflicts by
putting all our dependencies under their own context.

----------

In case someone runs into this problem, here's how the UI would look (notice the dropdown menus are not loaded properly and no categories are visible):

<img width="1086" alt="screen shot 2018-09-13 at 4 15 08 pm" src="https://user-images.githubusercontent.com/375307/45520902-6d228880-b770-11e8-9bb3-04e82baef103.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f5d0618e6f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.