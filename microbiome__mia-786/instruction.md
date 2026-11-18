# Issue

**Title:** Change unifrac implementation from rbiom to ecodive

## Description

As suggested in #783, this pull request changes the old unifrac implementation from `rbiom::unifrac` to corresponding `ecodive` functions. Based on my own testing the results are identical to the old version, and there seems to be a noticeable increase in speed as well. I think this means that #756 can be closed, as I doubt there would be anything to gain in continuing to develop our own unifrac implementation alongside `ecodive`'s.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95143283ea26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.