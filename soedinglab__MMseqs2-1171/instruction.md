# Issue

**Title:** Fix off-by-one in seq_reverse calls in BandedNucleotideAligner

## Description

SmithWaterman::seq_reverse(rev, seq, end) expects end = last index (L - 1), but lines 61, 68 and 93 pass L. So rev[0] = seq[L], one byte past the sequence, which holds whatever an earlier sequence left in the reused buffer.

MALLOC_PERTURB_=255 only clears a buffer when it is first allocated. With sequences of different lengths, a longer earlier sequence still fills that byte.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a0e39f2ea28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.