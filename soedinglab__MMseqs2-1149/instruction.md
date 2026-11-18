# Issue

**Title:** Use full query length for correlation-adjusted e-value

## Description

## Summary

With `--corr-score-weight > 0`, `alignStartPosBacktrace` recomputes the e-value after adding the correlation score, but it uses the aligned query span instead of the full query length.

That makes e-values of partial alignments too small, so false hits can pass `-e`.

## Cause

The local `query_length` starts as `profile->query_length`, but it is overwritten with the aligned span before the banded traceback:

```cpp
query_length = r.qEndPos1 - r.qStartPos1 + 1;   // window size for banded_sw
```

The correlation-score block later reuses it:

```
r.evalue = evaluer->computeEvalue(r.score1, query_length);
```

The e-value's search space should be based on the full query length.
The first-pass e-value in `ssw_align` and `scoreIdentical` already use the full length.

## Fix

Pass `profile->query_length` to `computeEvalue` in the correlation-score block.
Nothing else changes. `banded_sw` still gets the aligned span it needs.

## Testing

`easy-search` of the first 60 sequences of `examples/QUERY.fasta` against `examples/DB.fasta` with `--corr-score-weight 0.1`, before vs. after (GCC 16 build):

- 1434 hits in both runs, raw scores identical
- 380 partial alignments that get the correlation score: e-values larger after the fix (up to ~10⁹×, e.g. 1.0e-64 → 8.6e-55); none smaller
- Full-span alignments: unchanged
- Default `--corr-score-weight 0`: this code path doesn't run, so nothing changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76de5d8ae114`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.