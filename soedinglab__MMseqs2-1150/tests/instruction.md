# Issue

**Title:** Report most frequent diagonal in kmersearch results

## Description

## Summary

`KmerSearch::writeResult` should report, for each hit, the diagonal with the most k-mer matches.
It reports the last diagonal in the group instead.

`prevDiagonal` is assigned the current position just before the comparison, so the comparison is always true:

```cpp
prevDiagonal = kmers[i].pos;
cnt = (kmers[i].pos == prevDiagonal) ? cnt + 1 : 1;
```

As a result, `cnt` goes up on every k-mer, `cnt > bestDiagonalCnt` always holds, and bestDiagonal ends up as the last pos in the group. linsearch then passes that diagonal to rescorediagonal.
`prevDiagonal` was also declared without an initial value.

## Fix

- Initialize `prevDiagonal` from the first position of the hit group.
- Update `prevDiagonal` after `cnt` and the best diagonal have been computed, not before.

Within each (rep, id) group the k-mers are sorted by pos (compareRepSequenceAndIdAndDiag / ...Reverse in kmermatcher.h), so equal diagonals are adjacent and the longest run gives the most frequent diagonal.
This matches the pattern already used in `kmermatcher.cpp`.

## Behavior change

- When a hit's k-mers fall on more than one diagonal, linsearch now reports the most frequent diagonal, not the one that sorts last. rescorediagonal therefore scores a different diagonal for these hits, so some of them may be kept or filtered differently.
- On ties the first (smallest) diagonal wins, as before.
- The prefilter score (k-mer count) and the output format are unchanged.

## Testing

- Release build: clean.
- Synthetic linsearch --kmer-per-seq 300 test.
  - Each query / target pair shares a 100-aa block and a 30-aa block, offset by a 7-aa spacer:

| target → query   | before          | after            | score |
|------------------|-----------------|------------------|-------|
| X+Y → X+spacer+Y | 0               | 0                | 112   |
| X+spacer+Y → X+Y | 7 (30-aa block) | 0 (100-aa block) | 112   |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcf516aba34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.