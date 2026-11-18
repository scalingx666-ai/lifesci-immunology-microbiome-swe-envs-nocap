# Issue

**Title:** This should fix an intermittent problem with ICEFinder

## Description

The problem was that ICEFinder was mounting files from the params.outdir, those files were from publishDir. So, it happened from time to time that the files were not there to be mounted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f58eed791fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.