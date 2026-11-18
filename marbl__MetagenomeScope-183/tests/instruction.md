# Issue

**Title:** Reimplement image exporting

## Description

In addition to bringing this 100% back up to the previous functionality, I also added some fancy stuff that encodes the current date/time (down to the second) in the exported filename. It's pretty convenient :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7368f7cfefba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.