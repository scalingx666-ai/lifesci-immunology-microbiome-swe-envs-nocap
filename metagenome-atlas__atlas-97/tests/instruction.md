# Issue

**Title:** Corrects ambigous bases

## Description

I encountered [ambiguous bases](http://www.dnabaser.com/articles/IUPAC%20ambiguity%20codes.html) in the Cami dataset, which lead to errors in bbnorm. which didn't crash, but removed probably 90% of my reads. Applying `atlas QC` on the cami reads removed halve of the reads in the bbduck step. 

I suggest to convert them to N during the initial step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a8b1353b3ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.