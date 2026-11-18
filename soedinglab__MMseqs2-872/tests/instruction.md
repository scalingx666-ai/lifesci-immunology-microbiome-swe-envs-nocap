# Issue

**Title:** fix: prefilter segfault

## Description

## Description
bugfix for a segmentation fault in `mmseqs prefilter`, which occured in the following circumstances:

- `seqLen` of sequences larger than `32768` are overridden to `1` to lower their priority in diagonal score calculation
- `min(seqs[i].seqLen - minDistToDiagonal, minSeqLen);` returns an underflowed value for low `seqLen`, which holds for the above case (`UngappedAlignment L:279`)

=> this invalid `seqLength` value causes `unrolledDiagonalScoring(...)` to access memory out of bounds, causing a seg fault

## Changes
- added a safety check to prevent `seqLength` having invalid(underflowed) values
- `seqLen` larger than `32768` are overridden to `0` instead of `1`, in order to completely skip the processing inside `unrolledDiagonalScoring(...)`

## Other Details
- error encountered when running mmseqs easy-cluster on uniparc DB
- stack trace:
```
#0  UngappedAlignment::unrolledDiagonalScoring<21u> (...) 
    at MMseqs2/src/prefiltering/UngappedAlignment.cpp:58
#1  UngappedAlignment::scoreDiagonalAndUpdateHits (...) 
    at MMseqs2/src/prefiltering/UngappedAlignment.cpp:281
#2  UngappedAlignment::computeScores (...) 
    at /MMseqs2/src/prefiltering/UngappedAlignment.cpp:349
#3  UngappedAlignment::align (...)
    at /MMseqs2/src/prefiltering/UngappedAlignment.cpp:26
#4  QueryMatcher::match (...)
    at /MMseqs2/src/prefiltering/QueryMatcher.cpp:295
#5  QueryMatcher::matchQuery (...)
    at /MMseqs2/src/prefiltering/QueryMatcher.cpp:103
#6  Prefiltering::runSplit (...)
    at /MMseqs2/src/prefiltering/Prefiltering.cpp:843
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffb05619cada`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.