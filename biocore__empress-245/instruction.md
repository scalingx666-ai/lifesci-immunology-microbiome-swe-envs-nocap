# Issue

**Title:** fix #241

## Description

This , the issue was when the last value had padded zeros. 

Note that empress alone works fine but when combining with Emperor we get:
<img width="607" alt="Screen Shot 2020-07-08 at 7 19 42 PM" src="https://user-images.githubusercontent.com/2014559/86986186-4ce76900-c150-11ea-9b56-fecc7636435c.png">k 
However, not fixing here as I think that falls out of the scope of this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `852e39933ac9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.