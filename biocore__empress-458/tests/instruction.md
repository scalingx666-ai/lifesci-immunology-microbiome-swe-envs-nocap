# Issue

**Title:** REL: Add a short description to setup.py

## Description

Noticed that the short description field in `setup.py` previously just said `Empress`; this replaces that with a slightly modified version  of the description used for the GitHub repo.

I guess the motivation here is that some websites (e.g. pypi.org) which show information about PyPI packages start with the short description, so it would be nice to have such a description. For comparison, here are the PyPI pages for Empress and Gneiss. The short descriptions are shown in the gray bar in the middle of the page, just below the blue section and above the white section; Gneiss has a short description listed here, while Empress' just says `Empress`.

| Empress | Gneiss |
|---|---|
| ![image](https://user-images.githubusercontent.com/4177727/100489382-c6b0cc80-30c8-11eb-861a-07567eb3fea0.png) | ![image](https://user-images.githubusercontent.com/4177727/100489431-f8c22e80-30c8-11eb-99ac-d6da1ff5f1b9.png) |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1563ae251482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.