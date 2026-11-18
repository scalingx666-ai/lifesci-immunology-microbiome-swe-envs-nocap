# Issue

**Title:** citation: Add preferred-citation, change title.

## Description

The issue with the previous method is that individual versions are cited, and it is cited as software, not an article, which means google scholar and co don't pick it up well, I don't think, especially since individual version DOIs mean the citations get spread out. I'm looking for comments and maybe the protocol here can be rolled out across other tools as well.

Also the title had aviary in it twice.

A separate issue is that the citations isn't being automatedly updated when a new version comes out, but not entirely sure how to fix that with an action/script since it will have to happen post-release - maybe other repos have solved this somehow?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c9b50181987`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.