# Issue

**Title:** [MRG] enable minhash searches with different seeds

## Description

Another approach to address 

Briefly, the idea is that we calculate multiple minhash databases with different seeds (independent of the k-mer size) and then search at each of those different seeds.  For now, there is a new search routine, `search.extract_reads`, which takes as input query *sequences* rather than query *signatures* - this is because there is ~poor support in sourmash for saving and loading signatures with multiple seeds.

My proposed workflow is:

* calculate minhash DBs for multiple seeds
* search & extract matches using `search.extract_reads`, avoiding seed=42 which is the default MinHash seed;
* calculate containment and similarity of the extracted reads at seed=42.

- [x] Does this PR change the contracted DBG, catlas, or minhash DB formats?
      If so, merge with care as this will require rebuilding some big files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b80330764cd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.