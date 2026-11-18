# Issue

**Title:** [MRG] store ksize in MPHF index save files

## Description

Adds a `.ksize` attribute to `MPHF_KmerIndex` objects, and checks that this matches the requested ksize in various scripts.

Fixes 

**Note:** this PR changes save formats and will require rerunning build (or patch-fixing `contigs.sizes`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd0ab0f2f7ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.