# Issue

**Title:** Add ART modern

## Description

This adds the ART_modern read simulator and, if it works, can also be seen as a blueprint on how to add new simulators, since some changes have to be made at different positions in the pipeline.
ART_modern for metaT is currently untested

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8ceb8ac9185`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.