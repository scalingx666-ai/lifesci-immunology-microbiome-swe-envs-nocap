# Issue

**Title:** Add fixed md5sums and tests for lambda3

## Description

The new md5sums for working tests.

Concerning the deviating results for BlastX: This seems to be a problem of SeqAn2/lambda2 and not a very intuitive one. Basically, it looks like some sort of undefined behavior as the lambda3 results are always stable for BlastX and look valid. The results for lambda2 differ randomly over different runs of bidirectional indexing + search, while normal fm index and repetitive runs of search only stay stable. This means that over multiple rounds of bidirectional indexing and search in BlastX mode I had varying results from equal to lambda3 to varying missing hits (in the range of 4 to 10). Also no guarantee that it actually works perfectly stable for fm/search only, I ran only a limited amount of tests.

I did not look further into this and I have no idea how to best approach this. This is why I first added the lambda3 tests now, as this seemed to be stable and finally valid.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbc9eabc3a36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.