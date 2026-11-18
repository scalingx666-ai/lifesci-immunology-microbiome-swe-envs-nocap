# Issue

**Title:** Backtracking using a buffer

## Description

TLDR: This uses a different/faster backtracking algorithm.

Inspired by the findings #178, that using a heap data structure (DS) actually might be more performant, I decided to implement a new backtracking algorithm explicitly using the same heap DS. I also tried a second implementation that only needs a single buffer, but for compatibility reasons I decided to submit the double buffer implementation.

My new implementation shows up to 10% performance inccrease to the old implementation (at least in my test data). I ran each implementation 5 times and used the fastest run for comparison.
```
backtracking: fastest   runs
orig:         16.0s     16.0s/16.5s/16.3s/16.2s
buffer:       14.4s     15.0s/14.4s/14.9s/15.2s  # This PR
single:       14.6s     15.6s/15.2s/14.7s/14.6s  # Implementation with a single buffer
```


call: `./bin/lambda3 searchn -q illumina_reads_100_small.fasta -v 2 --adaptive-seeding false --seed-length 50 --seed-delta 2 --seed-half-exact 0 --threads 4 -i fm.index.lba`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `633a90d87254`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.