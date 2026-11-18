# Issue

**Title:** Update rootstock on 2023-01-13

## Description

This update includes support for corresponding authors, pinned publication dates, and other rootstock features. However, it contained more merge conflicts than I expected. Let's not merge it until after the traditional vaccines manuscript is completely finished (i.e. after I submit a separate pull request later today) in case it introduces formatting problems. I want to closely inspect the artifacts and the diff.

I'm attempting to comment out the new support for a pinned publication date. That's not relevant here where we have multiple publications. I'm also leaving out the corresponding author text from the front matter.

We will also be able to schedule manuscript builds now, for example on a weekly basis, which may be nice for this project.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a95292421060`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.