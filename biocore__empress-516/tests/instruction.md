# Issue

**Title:** throttled onwheel event

## Description

I don't know if this an issue was created for this but I just tried using empress on a mac laptop and the zoom functionality was incredibly sensitive, which caused the tree to zoom in/out incredibly fast. This PR fixes that issue by throttling the .onwheel event to fire at most 1 every 50 milliseconds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5eb4b6594cf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.