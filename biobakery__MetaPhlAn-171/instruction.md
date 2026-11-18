# Issue

**Title:** Check for a partial bowtie2 database build

## Description

Hello Aitor and Francesco,

I ran into an unlikely build issue (with an install I had done for one of our hutlab modules) but it had me stuck for a day or two trying to figure out what is going on so I wanted to send a small check for it to you. It turns out it is possible for a user to create a partial bowtie2 database file (for the MetaPhlAn mpa build) that has all of the files required, so it passes all of the MetaPhlAn database checks, yet it does not contain all of the species in the full database. The runs complete without error, bowtie2 does not have any issues with the partial database, but the results have very few species per sample. I was getting just a couple species for each sample from our set of HMP test files.

This code will check that two bowtie2 database files are approximately the same size. The "rev" files are the last to build and if "rev.1.bt2" is the same size (the exact same from all I checked out) as ".1.bt2" then the build is complete. I allowed for some size difference in the two just in case there are variations in the size of these two files from some custom builds; I don't think this is likely but at the same time I did not want to make this check too restrictive. I tested this will catch the partial build and at the same time this solution should be flexible for custom databases. Please let me know if you have any questions!

Thank you!
Lauren

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a1a1701c952`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.