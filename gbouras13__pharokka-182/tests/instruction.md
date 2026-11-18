# Issue

**Title:** modify the convert_gff_to_gbk.py function and deps

## Description

Hi @gbouras13 

Thanks for your work on pharokka. It seems like a very promising program. I noticed that the processing function to convert `gff` to `gbk` is being done with `emboss`, which is a heavy program for just one function. Then, I thought that a light custom function based on biopython could make it as well. It also uses the bcbio-gff library. 

Thanks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12cc5338d307`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.