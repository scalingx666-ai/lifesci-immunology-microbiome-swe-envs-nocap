# Issue

**Title:** Option to provide high quality nanopore reads to flye with --nano-hq, default to --nano-raw.

## Description

Assembling with `run_flye.py` currently defaults to ONT high-quality reads: Guppy5+ SUP or Q20. Going forward, this is likely what most people will be using, however it would be nice to support pre-Guppy5 for the time being.

Also see:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf618f0f8e32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.