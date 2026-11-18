# Issue

**Title:** Fix/semicolons sorting

## Description

Removing semicolons if last character in attributes before appending mobilome-related annotation. 
Stop sorting contigs, just sorting mobilome elements based in the start position.

Thanks for reviewing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfb4137f986d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.