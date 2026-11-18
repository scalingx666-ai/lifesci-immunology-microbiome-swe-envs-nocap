# Issue

**Title:** add option to suppress @info

## Description

Uses the .ini argument `suppress_messages` (defaults to false). I did it this way (instead of changing logging properties) so it will play nicely with Omniscape. @ranjanan it would be awesome if you could review and merge if it looks good to you!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa075e1c052b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.