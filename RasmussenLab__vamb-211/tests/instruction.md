# Issue

**Title:** Timestamp and reformat epoch log message

## Description

I've found it practical to know how long a given epoch has taken to train. Also, format the losses nicer:
* Print the weighed loss, not the unweighed. This is more intuitive, and has the property that the stated loss is indeed the sum of its components.
* Print the loss in scientific notation, since they now can scale differently
* Use uniform distance between the fields when printing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cab3e0b8b922`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.