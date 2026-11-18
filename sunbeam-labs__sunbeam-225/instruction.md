# Issue

**Title:** Hotfix for #224 - Make implicit dependencies explicit

## Description

This explicitly adds samtools and bcftools to the list of dependencies in environment.yml, instead of relying on their (now absent) dependency via pysam.  .  I'll tag this as 2.0.2 afterward and merge back into dev as well so it's all synced up.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4401c9198f15`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.