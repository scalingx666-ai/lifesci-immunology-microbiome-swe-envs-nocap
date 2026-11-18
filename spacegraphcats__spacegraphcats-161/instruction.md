# Issue

**Title:** [MRG] allow multiple minhash databases => multihash search

## Description

This PR supports the computation/storage of multiple minhash databases, so that we can e.g. have multiple k-mer sizes or scaled values.  Also updates extract code so that searches use a shadow built from the union of frontiers found at multiple k-mer sizes, which is the simplest and dumbest way to use multiple k-mer sizes to search the catlas.

TODO:
- [x] update `search/frontier_search_batch.py`
- [ ] maybe support ranges in the ksize spec.
- [x] also, update the podar signatures to have this range of k-mer sizes.

Note:
- [x] Does this PR change the contracted DBG, catlas, or minhash DB formats?
      If so, merge with care as this will require rebuilding some big files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6bb5533e70bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.