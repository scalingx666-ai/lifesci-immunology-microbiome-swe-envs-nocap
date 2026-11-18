# Issue

**Title:** Update of MMP Mar-databases (https://mmp.sfb.uit.no)

## Description

Hi, 

We just released the official version 2 of the Mar-databases. I have updated all necessary static files on our backend needed by makeDB.sh, and fixed some minor parsing issues in the script which is now ready for a merge with master.
A working implementation of Kajiu with the v2 Mar-databases is available in my fork until merge.
-Espen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbcbd831924c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.