# Issue

**Title:** Improvements to reporting to aid in evaluation

## Description

This PR -

* pulls almost everything back to match_rank for evaluation and reporting, which is more stringent than before;
* reorders the reason numbers so that the gather test, the first check & the most common reason for removal, is \# 1 (#50) 
* adds full contig classification per #51 to include NO_IDENT and NO_HASH, not just clean and dirty
* changes lineage display to be more informative (but now it's maybe too verbose)

TODO:
- [x] add tests for new `ContigInfo` enum and clean_flag reasoning,  
- [x] nicer lineage foo #68 

 #51 #68

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `214efe331767`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.