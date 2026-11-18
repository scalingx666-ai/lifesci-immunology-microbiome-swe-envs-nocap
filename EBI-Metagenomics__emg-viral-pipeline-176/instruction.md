# Issue

**Title:** Add chunking of input fasta for VirFinder and PPRmeta

## Description

I transfered Kate's changes from #172 for chunking to include them to a small release that we can use in production (3.3.2). 

- Kate did chunking for VirFinder, I added one for PPRmeta
- I also had to redefine circularity to `False` in the `bin/parse_viral_pred.py` to fix this bug from VirSorter2 
- Update containers in SPLIT_PROTEINS because current singularity container is not accessible

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfac7c8ddae6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.