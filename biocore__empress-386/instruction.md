# Issue

**Title:** Configurable barplot borders

## Description

, and should at least make generating figures for the paper a lot easier.

This also removes some of the extra whitespace in the barplot panel when `Draw barplots?` is unchecked -- this was due to a `<p>` tag being empty but not hidden, which caused some extra vertical space to be taken up.

![borders](https://user-images.githubusercontent.com/4177727/93843515-ee119600-fc4e-11ea-95d5-4e71136f26d0.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3968bd42023b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.