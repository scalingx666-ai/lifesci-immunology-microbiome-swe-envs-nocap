# Issue

**Title:** ENH: Hide axes labels and lines

## Description

The color slector for the axes labels and lines can now be set to empty
(or null), this results in the labels and lines to be hidden. This PR also
adds the appropriate tests.

See animated gif:

![quick](https://user-images.githubusercontent.com/375307/28443336-3606cbfa-6d6a-11e7-98cb-952fca0caf3f.gif)


.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7a3cf4dbfe9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.