# Issue

**Title:** Use fmindex_collection as an FMIndex

## Description

This replaces [SeqAn3](https://github.com/seqan/seqan3/) based data structures and search routines with those from [fmindex_collection](https://github.com/SGSSGene/fmindex-collection)

fmindex_collection also has an integrated version of libsais which is "faster" than libdivsufsort (which is integrated in sdsl/SeqAn3)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1538cd160283`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.