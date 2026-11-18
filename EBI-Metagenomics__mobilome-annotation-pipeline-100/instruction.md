# Issue

**Title:** Fixing the tRNA coordinates at the edge of the contig

## Description

Aragorn report end coordinates one position beyond the end of the contig, triggering antismash to fail. In this PR we are also fixing start = 0 just in case. 

Thanks for reviewing!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba1bd512b3ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.