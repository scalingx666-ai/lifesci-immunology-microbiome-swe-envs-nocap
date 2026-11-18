# Issue

**Title:** DRAM functional annotation

## Description

Integrating https://github.com/shafferm/DRAM into atlas. 


DRAM does a lot of cool things but not everything I would like. 

Downloading a lot of DBs and do the annotation. 
KOfam, CAZy are the most interesting,  I think. 

It creates a summary of some modules but not all that are in Kegg. 
It contains the information of KO to Kegg module mapping but I don't know how ambiguous mapping are handled.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b848e0a8872a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.