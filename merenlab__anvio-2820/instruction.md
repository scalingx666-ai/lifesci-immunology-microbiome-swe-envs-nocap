# Issue

**Title:** ship the library for structure display with anvi'o

## Description

Final part of #2769: `anvi-display-structure` no longer fetches anything from the internet and works offline.
The npm check now checks every package in `package.json`, so existing installs are told to re-run `npm install`.
So: **after pulling, run `npm install` in `anvio/data/interactive`.**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d88db48f766`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.