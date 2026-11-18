# Issue

**Title:** Reveal a node on the tree when the user clicks on a biplot arrow

## Description

If a biplot arrow is clicked, the node is revealed in the tree:

![biplot](https://user-images.githubusercontent.com/375307/87846629-10211d80-c886-11ea-85d9-ad7759a74d95.gif)

![biplot](https://user-images.githubusercontent.com/375307/88004768-945ce600-cabc-11ea-9894-bb6ba5ffcee8.gif)


As a side effect, the samples in the emperor plot that have that feature are also highlighted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4987a806ca3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.