# Issue

**Title:** fixing parsing of variable int fcs files; speeding it up

## Description

This is a fix for 
It enables parsing of variable int length FCS files; it also speeds up their parsing significantly. 
Includes a new unit test for this issue; and an (artificially shortened) FCS file to facilitate that test. FCS file is a real file I was using; but I've taken out almost all the data. 

In checking that the results of new parsing were accurate, I discovered an additional discrepancy; a "fixed" version of the existing method I think was giving incorrect results for 32 bit ints when they were large; results for them were inconsistent with my new version; another fcs parsing library (fcsparser), and the d_range parameter within the FCS file. 

Note that to accomplish faster parsing, this code relies on the iter_unpack function; this was introduced in python 3.4. If this is undesirable there may be another way to accomplish faster parsing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a55c9b794507`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.