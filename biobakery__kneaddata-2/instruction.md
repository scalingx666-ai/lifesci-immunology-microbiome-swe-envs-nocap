# Issue

**Title:** Defaults changed

## Description

Changes for this pull request: 

- Make TRF on by default and before bowtie2 step.
- Change name from --cut-adapters to --trim-repetitive.
- Make --trim-repetitive on by default and before trimmomatic step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `513d36c8871c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.